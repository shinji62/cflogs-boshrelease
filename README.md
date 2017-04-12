CFLOGS bosh release
=======================

Background
----------

### What is Cflogs?

Cloud Foundry loggregator firehose is fire and forget and can drop logs is you don't consume fast enough.

Most of the loggings system, like syslog, elasticsearch and so on are pretty slow and losting logs can happen especially in high traffic env.


So the idea is to use something fast enough to consumes the firehose stream without putting pression on the final consumer.


Using Kafka, we can easily consume the firehose stream and we can use as much consumer as we want on the same kafka deployment.


![cflogs Overview](./docs/Kafka-Nozzle.png)


Each Event Type message crate a topics so as today :

LogMessage
Counter
..
..
..



Consuming from Kafka
--------------------

If you have already some Nozzle the change should not be big as we can reuse you can find an example with [cf-kafka-to-syslog](https://github.com/shinji62/cf-kafka-to-syslog).






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
Well Zookeeper...

Not Include in this bosh release we use [Zookeeper-release](https://bosh.io/d/github.com/cppforlife/zookeeper-release)


Usage
-----

First upload zookeeper-release if you don't have it

```bash
$ bosh upload release https://bosh.io/d/github.com/cppforlife/zookeeper-release
```

Then upload this bosh release

```bash
$ bosh upload release https://github.com/shinji62/cflogs-boshrelease
```

Please check the deployment sample manifest [templates/bosh-lite.yml](./templates/bosh-lite.yml)


Then just deployment

```
//Bosh-old-cli
bosh deploy

//Bosh cli v2
bosh2 deploy -e yourenv -d cflogs-boshlite ./templates/bosh-lite.yml -n 
```



TODO
====
* Test test and test
* Concourse Pipeline
