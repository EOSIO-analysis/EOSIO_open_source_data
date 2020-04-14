# EOSIO_open_source_data

This is the open source data for EOSIO blockchain, which is used in our paper:

Yuheng Huang, Haoyu Wang, Lei Wu, Gareth Tyson, Xiapu Luo, *Understanding (Mis)Behavior on the EOSIO Blockchain*

Thanks for the help from [Peckshield inc](https://peckshield.com/en#home), which including helping collecting data and replaying some attacks mentioned in the paper.

### graph data

Here is the list of our graph data:

> * EMFG_times.gpickle  -- 958 MB
> * EMFG_lite.gpickle -- 438 MB
> * EMFG_full.gpickle -- 1GB
> * EACG.gpickle -- 87MB
> * ECIG.gpickle -- 1GB

Considering the size of the data, it is very hard to upload them all to the github. So we upload full-version data to *mendeley*.

We will explain all the graph data below:

#### EMFG

The defination of EMFG is:

$EMFG=(V, E, D, w), E={(v_{i}, v_{j}, D_{k}), v_{i}, v_{j} \in V, D_{k} \subseteq D}$

In short, you can use the data by using networkx as follows:

```python
>>> import networkx as nx
>>> EMFG = nx.read_gpickle("EMFG_full.gpickle")
>>> print(EMFG['eosio']['heztcnjtgage']['2018 06 09'])
0.1
```

#### ECIG

#### EACG

### groundtruth for bot detection
