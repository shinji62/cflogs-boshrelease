CFLOGS bosh release
=======================

Background
----------

### What is Cflogs?

Cloud Foundry loggregator firehose is fire and forget and can drop logs is you don't consume fast enough.

Most of the loggings system, like syslog, elasticsearch and so on are pretty slow and losting logs can happen especially in high traffic env.


So the idea is to use something fast enough to consumes the firehose stream without putting pression on the final consumer.


Using Kafka, we can easily consume the firehose stream and we can use as much consumer as we want on the same kafka deployment.




Component
---------

kafka-firehose-nozzle (Fork from )
kafka  
Zookeeper  ()




Usage
-----

To use this bosh release, first upload it to your bosh:

```
bosh upload release https://github.com/shinji62/cflogs-boshrelease
```
