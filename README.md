# MongoDB Sharded Cluster with Docker
### A complete hands-on lab for building distributed database infrastructure

This project implements a **fully sharded MongoDB cluster** using Docker, closely following production-grade distributed database architectures.  
The goal is to understand MongoDB sharding “from the ground up” by first deploying everything manually using `docker run` and Docker networks, and then evolving the project toward a professional multi-environment setup using Docker Compose.

---

Primero haremos un docker un docker run + red manual ya que para mi es importante entender bien y practicar los conceptos, la base.
Una vez hecho lo empaquetarmos en docker compose y luego en dev/prod.

### Idea general (qué vamos a montar)

Vamos a replicar exactamente la práctica:

Replica set de config servers: myCS (3 nodos)

- Shard 1: replica set myRS1 (3 nodos)

- Shard 2: replica set myRS2 (3 nodos)

- 1 mongos como query router

Todo:

- En una sola máquina (tu Mac, con Docker Desktop).

- En una red Docker llamada mongo-net.

- Sin Docker Compose, sólo docker network y docker run.

Los servicios dentro de la red van a hablar entre ellos por hostname:

- config1, config2, config3

- shard1_1, shard1_2, shard1_3

- shard2_1, shard2_2, shard2_3

- mongos (el ruter)

Y todos escuchan en el puerto interno 27017 (para simplificar).
Desde tu Mac, tú sólo vas a usar localhost:27027 (que mapearemos al mongos).$