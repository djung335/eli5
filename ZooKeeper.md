Apache ZooKeeper

What is Apache ZooKeeper?

Simply put, ZooKeeper is a service to manage distributed applications. The name is appropriate; ZooKeeper acts similarly to how an actual zookeeper goes around to all the animals and tends to them.

Imagine this situation: we have a large amount of files in a file store and the number of files keeps increasing by the hour. Our task is to first process and then delete these files. One of the approach we can think of is to write a script that does this task and run multiple instances parallelly on multiple servers. We can even increase or decrease the server count based on the demand. This is basically a distributed compute/data processing application.

Here, how can we ensure that the same file is not picked and processed by multiple servers at the same time? To solve this problem, all the servers should share the information between them regarding which file is currently being processed.

This is where ZooKeeper becomes useful. When the first server wants to read a file, it can write to the zookeeper the file name its going to process. Now the rest of the servers can look up ZooKeeper and know that this file is already picked up by the first server.
