# EOSIO_open_source_data

This is the open source data for EOSIO blockchain, which is used in our paper:

Yuheng Huang, Haoyu Wang, Lei Wu, Gareth Tyson, Xiapu Luo, Run Zhang, Xuanzhe Liu, Gang Huang, Xuxian Jiang, *Understanding (Mis)Behavior on the EOSIO Blockchain*

Thanks for the help from [Peckshield inc](https://peckshield.com/en#home), which including collecting data and replaying some attacks mentioned in the paper.

## graph data

Here is the list of our graph data:

> * EMFG_times.gpickle  -- 958 MB
> * EMFG_lite.gpickle -- 438 MB
> * EMFG_full.gpickle -- 1GB
> * EACG.gpickle -- 87MB
> * ECIG.gpickle -- 1GB

Considering the size of the data, it is very hard to upload them all to the github. So we upload full-version data to *MEGA*. Please download from here: https://mega.nz/folder/PAQ2kSxT#OCXMwRvOK65qFW561Pm2Ow

We will explain all the graph data below:

### EMFG

The defination of EMFG is:

<img src="https://render.githubusercontent.com/render/math?math=EMFG=(V, E, D, w), E={(v_{i}, v_{j}, D_{k}), v_{i}, v_{j} \in V, D_{k} \subseteq D} ">

In short, you can use the data by using networkx as follows:

```python
>>> import networkx as nx
>>> EMFG = nx.read_gpickle("EMFG_full.gpickle")
>>> print(EMFG['eosio']['heztcnjtgage']['2018 06 09'])
0.1
```
*EMFG_full* is the graph in the paper. In addition, we provide *EMFG_lite*, which doesn't have timestamps and thus is much smaller than  *EMFG_full*

*EMFG_times* records the transfer times from one account to another. This should be a part of ECIG as all transfer on EOSIO could be seen as a invocation from sender to eosio.token, and contract eosio.token will handle the transfer. However, it is more convenient ane meaningful to separate it from other invocations (Just like Ethereum).

### ECIG

The defination of ECIG is:

<img src="https://render.githubusercontent.com/render/math?math=ECIG = (V,E,D,A,f), E={(v_{i}, v_{j}, D_{k}, A_{k}),}v_{i}, v_{j} \in V, D_{k} \subseteq D, A_{k} \subseteq A.">

In short, you can use the data by using networkx as follows:

```python
>>> import networkx as nx
>>> ECIG = nx.read_gpickle("ECIG.gpickle")
>>> print(ECIG['betdicegroup']['betdicesicbo']['2019 03 12']['maintenance'])
925
```

### EACG

The defination of EACG is 

<img src="https://render.githubusercontent.com/render/math?math=EACG=(V,E,D), E={(v_{i}, v_{j}, d), v_{i}, v_{j} \in V, d \in D} ">

In short, you can use the data by using networkx as follows:

```python
>>> import networkx as nx
>>> EACG = nx.read_gpickle("EACG.gpickle")
>>> print(EACG['tp']['zhanggang.tp'])
{'2019 04 23': 1}
```

## Bot

### groundtruth for bot detection

Due to the Confidentiality agreement with our partner, peckshield, we can not publish the groundtruth here directly. Please contact huangyuheng@bupt.edu.cn if you are interested.

### Feature for per-account level bot detection

The features for per-account level detection in our paper are as follows:
| feature                | bots(avg) | normal(avg) |
| ---------------------- | --------- | ----------- |
| ACG depth              | 4.3       | 1.8         |
| transferIn std         | 40.8      | 954         |
| transferOut std        | 57.3      | 1267.3      |
| volume per transferIn  | 2.2       | 104         |
| volume per transferOut | 6.2       | 553.1       |
| transfer target num    | 5.9       | 12.6        |
| invoke contract num    | 16.1      | 3.2         |
| invocation num         | 518.5     | 2312.7      |
| invocation std         | 6.2       | 40.3        |
| activate time          | 74.6%     | 13.4%       |
| siblings in same day   | 1724.1    | 117024.4    |

- ACG depth means the depth of one account in ACG.
- transferIn std means the standard deviation of transfer in volume time array.
- transferOut std means the standard deviation of transfer out volume time array.
- volume per transferIn means the total transfer in volume divided by transfer out times.
- volume per transferOut means the total transfer in volume divided by transfer out times.
- transfer target num means the number of transfer target.
- invoke contract num means the number of contracts the account invoked.
- invocation num means the number of invocations.
- invocation std means the standard deviation of invocation time array.
- activate time means the time one account being active (i.e. invoke contract of transfer money). It is represented by activate date / total time
- siblings in same day means the number of siblings of one account created in one day. (sibling: accounts created by same parent)

