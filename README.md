Trino cluster with `docker-compose`
===================================

This project can be used to setup a [Trino](https://trino.io/) cluster with `docker-compose`.

The Trino cluster makes use of the [tpch](https://trino.io/docs/current/connector/tpch.html)
catalog for benchmarking the performance of the cluster computations.

## Cluster setup
Setting up initially the cluster (composed of a coordinator and a worker) can be done through the command:

```bash
docker-compose up
```

In detached mode:

```bash
docker-compose up -d
```


Scale the number of workers into the Trino cluster:

```bash
docker-compose up --scale trino-worker=3 -d
```


Check the number of nodes in the Trino cluster:

```bash
docker exec -it trino-docker-compose-cluster_trino-coordinator_1 /usr/bin/trino
```

```sql
trino> select * from system.runtime.nodes;
node_id    |         http_uri         | node_version | coordinator | state  
--------------+--------------------------+--------------+-------------+--------
 ff1ffc8ae0e0 | http://192.168.32.3:8080 | 358          | true        | active 
 cdf437dd81da | http://192.168.32.2:8080 | 358          | false       | active 
 e165fc03b39d | http://192.168.32.5:8080 | 358          | false       | active 
 fa33d391ac43 | http://192.168.32.4:8080 | 358          | false       | active 
(4 rows)
```


## Benchmarks

Execute any of the queries from the directory [benchmarks](benchmarks) to get a feeling on how
the cluster is performing.


## Tear down

```bash
docker-compose down
```
