prometheus-kafka-consumer-group-exporter
========================================

A [prometheus](https://prometheus.io/) exporter for Kafka's consumer group information.

Capability
==========
- Exports Kafka's consumer group information which can be obtained by executing `kafka-consumer-groups.sh`
- Supports only new consumer(`--new-consumer` switch enabled by default) which uses Kafka broker as the offset checkpoint store

Export metrics
==============
- `kafka_broker_consumer_group_current_offset` : Consuming offset of each consumer group/client/topic/partition based on committed offset
- `kafka_broker_consumer_group_offset_lag` : Offset lag between the last log end offset and consuming point of each consumer group/client/topic/partition

Build
=====
```sh
$ mkdir -p $GOPATH/src/github.com/kawamuray
$ cd $GOPATH/src/github.com/kawamuray
$ git clone https://github.com/kawamuray/prometheus-kafka-consumer-group-exporter.git
$ cd prometheus-kafka-consumer-group-exporter
$ go get . && go build -o kafka_consumer_group_exporter .
```

Example Usage
=============
```sh
# Download latest Kafka distribution(if necessary)
tar zxvf kafka_LATEST_VERSION.tgz
./kafka_consumer_group_exporter --consumer-group-command-path=./kafka_LATEST_VERSION/bin/kafka-consumer-groups.sh BOOTSTRAP_SERVERS
```
