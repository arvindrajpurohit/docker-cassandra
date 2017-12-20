# Cassandra as Docker Container

**DOCKER RUN**, cassandra with *docker run* command with volume mounting for persistency

 ```bash
docker run --name sample-cassandra --privileged -d -v /var/db/cassandra:/var/lib/cassandra -p 7000:7000 -p 9160:9160 -p 9042:9042 -p 7199:7199 cassandra:3.9
 ```
# Multinode cluster in swarm mode

```bash
cd multi-node-swarm-mode/

docker stack deploy -c cassandra-stack.yml cs_cluster
```

## Container Shell Access

Connecting to running cassandra cluster and do *nodetool* or *cqlsh*

```bash
docker exec -it sample-cassandra bash
```

 *sample-cassandra - name of the container*


# No connections until Cassandra init completes
 In case this is the first time starting up cassandra we need to ensure that all nodes do not start up at the same time. Cassandra has a 2 minute rule i.e. 2 minutes between each node boot up. Booting up nodes simultaneously is a mistake. This only needs to happen the firt time we bootup. Configuration below assumes if the Cassandra data directory is empty it means that we are starting up for the first time.

