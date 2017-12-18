 
 # No connections until Cassandra init completes
 In case this is the first time starting up cassandra we need to ensure that all nodes do not start up at the same time. Cassandra has a 2 minute rule i.e. 2 minutes between each node boot up. Booting up nodes simultaneously is a mistake. This only needs to happen the firt time we bootup. Configuration below assumes if the Cassandra data directory is empty it means that we are starting up for the first time.

