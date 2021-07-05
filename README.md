Trino cluster with `docker-compose`
===================================


Setup 

```bash
docker-compose up
```

In detached mode:

```bash
docker-compose up -d
```


Add another worker to the Trino cluster

```bash
docker-compose up trino-worker -d
```

Teardown

```bash
docker-compose down
```