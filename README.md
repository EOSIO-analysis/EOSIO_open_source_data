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

Considering the size of the data, it is very hard to upload them all to the github. So we upload full-version data to *mendeley*.

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

<img src="https://render.githubusercontent.com/render/math?math=ECIG = (V,E,D,A,f), E={(v_{i}, v_{j}, D_{k}), v_{i}, v_{j} \in V, D_{k} \subseteq D} ">

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
>>> printE(ACG['tp']['zhanggang.tp'])
{'2019 04 23': 1}
```
### groundtruth for bot detection
