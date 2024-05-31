---
title: "Docker-Compose: Redis Cluster"
weight: 1
---

```yml
version: '3'

x-environment-redis:
  &default-redis-env
    ALLOW_EMPTY_PASSWORD: 'yes'
    REDIS_NODES: '127.0.0.1:10000 127.0.0.1:10001 127.0.0.1:10002 127.0.0.1:10003 127.0.0.1:10004 127.0.0.1:10005'

services:
  redis-node-1:
    image: public.ecr.aws/bitnami/redis-cluster:7.2
    restart: always
    network_mode: host
    environment:
      <<: *default-redis-env
      REDIS_PORT_NUMBER: 10001

  redis-node-2:
    image: public.ecr.aws/bitnami/redis-cluster:7.2
    restart: always
    network_mode: host
    environment:
      <<: *default-redis-env
      REDIS_PORT_NUMBER: 10002

  redis-node-3:
    image: public.ecr.aws/bitnami/redis-cluster:7.2
    restart: always
    network_mode: host
    environment:
      <<: *default-redis-env
      REDIS_PORT_NUMBER: 10003

  redis-node-4:
    image: public.ecr.aws/bitnami/redis-cluster:7.2
    restart: always
    network_mode: host
    environment:
      <<: *default-redis-env
      REDIS_PORT_NUMBER: 10004

  redis-node-5:
    image: public.ecr.aws/bitnami/redis-cluster:7.2
    restart: always
    network_mode: host
    environment:
      <<: *default-redis-env
      REDIS_PORT_NUMBER: 10005

  redis-cluster:
    image: public.ecr.aws/bitnami/redis-cluster:7.2
    restart: always
    network_mode: host
    depends_on:
      - redis-node-1
      - redis-node-2
      - redis-node-3
      - redis-node-4
      - redis-node-5
    environment:
      <<: *default-redis-env
      REDIS_PORT_NUMBER: 10000
      REDIS_CLUSTER_REPLICAS: 1
      REDIS_CLUSTER_CREATOR: 'yes'
```
