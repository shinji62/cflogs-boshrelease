CFLOGS bosh release
=======================

Background
----------

### What is Cflogs?

Cloud Foundry loggregator firehose is fire and forget and can drop logs is you don't consume fast enough.

Most of the loggings system, like syslog, elasticsearch and so on are pretty slow and losting logs can happen especially in high traffic env.


So the idea is to use something fast enough to consumes the firehose stream without putting pression on the final consumer.


Using Kafka, we can easily consume the firehose stream and we can use as much consumer as we want on the same kafka deployment.


![cflogs Overview](https://cdn.rawgit.com/shinji62/cflogs-boshrelease/30b06d33/docs/Kafka-Nozzle.svg)

Component
---------

#### kafka-firehose-nozzle
Simply forward message from the firehose to kafka.
For topics and partition information please go directly to the Github  [repository](https://github.com/shinji62/kafka-firehose-nozzle).

For now we install the nozzle on VM


### Kafka  
Well Kafka....
Included in this bosh release Kafka v0.10.2.0


### Zookeeper
Well Zookeeper
Not Include in this bosh release we use [Zookeeper-release](https://bosh.io/d/github.com/cppforlife/zookeeper-release)


Usage
-----

First upload zookeeper-release if you don't have it

```bash
$ bosh upload release https://bosh.io/d/github.com/cppforlife/zookeeper-release
```

Then upload this bosh releasecd
```bash
$ bosh upload release https://github.com/shinji62/cflogs-boshrelease
```
