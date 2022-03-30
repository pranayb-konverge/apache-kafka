# Apache Kafka 

## It is a DISTRIBUTED PUBLISH-SUBSCRIBE MESSAGING system.

## To start zookeeper / orchestrator
```bin/zookeeper-server-start.sh config/zookeeper.properties```

## To start server/ broker
```bin/kafka-server-start.sh config/server.properties```

## To create topic
```bin/kafka-topics.sh --create --bootstrap-server localhost:9092 --topic cities```

## To list the topic
```bin/kafka-topics.sh --list --bootstrap-server localhost:9092 --topic cities```

## To describe the topic
```bin/kafka-topics.sh --describe --bootstrap-server localhost:9092 --topic cities```

## Producer & Consumer:

- Mutiple producers can send messages to the broker and these messages can be consumed by multiple consumers on the basis of TOPIC. In the above commands the --topic is provided to the producer & consumer. 
- We can create mutiple produces and consumers in diffrent terminal windows. So teh conclusion is that the producers and consumers dont know about each other. They simply send and recive the messages to/from centralise storage of kafka named kafka cluster.

## To create a producer
```bin/kafka-console-producer.sh --broker-list localhost:9092 --topic cities```

## To create a consumer
```bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic cities --from-beginning```

## BROKER
- It is the interface between producer & consumer, if on is down others can handle its job, which is called BROKER cluster.

## ZOOKEEPER
- Maintains the list of active brokers
- Elects BROKER
- Manages the configuration of TOPICS and partitions

## QUORUM 
It is the number of acknowledgments required and the number of logs that must be compared to elect a leader such that there is guaranteed to be an overlap for availability. Most systems use a majority vote, Kafka does not use a simple majority vote to improve availability

## ZOOKEEPER cluster (ensemble)
- It is recommended to have odd number of servers/brokes and quorun set to (n+1)/2 where n is qty of servers.
- If the cluster is of 4 zookeeprs and Quorum is set to 2 and there is a failure then producer & consumer will give descripancy messages.

##  Default ports
- Zookeeper - ```localjost:2181```
- Kafkar server/broker - ```localhost:9092```
- If Broker should be publically accessible you need to adjust "advertised.listeners" property in server.configuration files.

## TOPIC
- Topic has its own unique name so the producer & consumer can distingush the message.
- The messaging system is like a queue
- Log retension period is 7 days. One can delete the whole logs as well but cannot edit the messages as they are encripted.

## Message Structure
- Timestamp
- offset number (unique accross positions)
- key (optional)
- Value (sequence of bytes)

- We can send files as well which are encoded in bytes format.
- idea is to keep messages as small as possible.
