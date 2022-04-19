# What is Apache ZooKeeper?

Simply put, ZooKeeper is a **service to manage distributed applications**. ZooKeeper acts similarly to how an actual zookeeper goes around to all the animals and tends to them.

Imagine this: we have a large amount of files in a file store and the number of files keeps increasing by the hour. Our task is to first process, then delete these files. To do this, one thought is to write a script that does the task. and run multiple instances on multiple servers. This is basically a distributed application.

However, how can we ensure that the same file is not picked and processed by multiple servers at the same time? To solve this problem, all the servers should share the information between them regarding which file is currently being processed.

This is where ZooKeeper becomes useful. When the first server wants to read a file, it can write to the ZooKeeper the file name its going to process. Now the rest of the servers can look up ZooKeeper and know that this file is already picked up by the first server.

# Some Definitions To Know:

**Cluster** - A group of systems in which a distributed application is running.

**Node** - A machine running in a cluster.

**Client** - One of the nodes in our distributed application cluster.

**Server** - One of the nodes in our ZooKeeper ensemble.

**Ensemble** - A group of ZooKeeper servers.

**znode** - A ZooKeeper node.

![image](https://user-images.githubusercontent.com/44933949/163919426-8a2c4862-cb27-4bf0-a9b1-842ea8834944.png)

ZooKeeper has a Client-Server Architecture.

# Features of ZooKeeper

## Naming Service

## Configuration Management

## Leader Election
In a ZooKeeper ensemble, one node will be the leader and the others will be the followers. The process is described [here](https://www.tutorialspoint.com/zookeeper/zookeeper_leader_election.htm), but the gist is that to do it from scratch is pretty hard and ZooKeeper simplifies the process.

# How Many ZooKeeper Nodes Should I Have In My Ensemble?

This is an important question because of how writes are handled in a ZooKeeper ensemble. If a client wants to send data in the ensemble, a server recieves the request and sends that to the leader. which will then reissue the request to all the followers. The write request will succeed **only if a majority of the nodes** (also known as a quorum) **respond successfully**.

A few examples:

If we have **one node**, then we have a [single point of failure](https://en.wikipedia.org/wiki/Single_point_of_failure). In other words, if this single node goes down, the entire ZooKeeper ensemble goes down which is not desirable.

If we have **two nodes**. if one goes down then we do not have a majority (1/2).

If we have **three nodes**. if one goes down then we do have a majority (2/3). Three nodes is the minimum number of nodes for a working ZooKeeper ensemble.

If we have **four nodes**, we can do a comparison with three nodes. If two nodes go down, then we do not have a majority in either situation, and so having 3 or 4 nodes is essentially the same thing. Having the extra node is pointless, and this is a good example of why nodes should be added in odd numbers.



**Some Other Important Things**
ZooKeeper was designed to store coordination data. and it should probably not be used as a database.

## Credits/Sources
https://www.tutorialspoint.com/zookeeper/index.htm
