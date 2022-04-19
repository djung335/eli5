# What is Apache ZooKeeper?

Simply put, ZooKeeper is a **service to manage distributed applications**. ZooKeeper acts similarly to how an actual zookeeper goes around to all the animals and tends to them.

Imagine this: we have a large amount of files in a file store and the number of files keeps increasing by the hour. Our task is to first process, then delete these files. To do this, one thought is to write a script that does the task. and run multiple instances on multiple servers. This is basically a distributed application.

However, how can we ensure that the same file is not picked and processed by multiple servers at the same time? To solve this problem, all the servers should share the information between them regarding which file is currently being processed.

This is where ZooKeeper becomes useful. When the first server wants to read a file, it can write to the ZooKeeper the file name its going to process. Now the rest of the servers can look up ZooKeeper and know that this file is already picked up by the first server.

# Some Definitions To Know:

**Cluster** - A group of systems in which a distributed application is running.

**Node** - Each machine running in a cluster.

**Ensemble** - A group of ZooKeeper servers.

**znode** - A ZooKeeper node.

![image](https://user-images.githubusercontent.com/44933949/163919426-8a2c4862-cb27-4bf0-a9b1-842ea8834944.png)

ZooKeeper has a Client-Server Architecture.



**Some Other Important Things**
ZooKeeper was designed to store coordination data. and it should probably not be used as a database.
