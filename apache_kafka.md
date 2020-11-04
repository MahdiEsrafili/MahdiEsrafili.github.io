# Apache Kafka

Apache Kafka is a great data streaming platform. It can stream data from file to database or multiple services. Kafka has pub/sub mechanism.

## Kafka Connect

Kafka Connect is a great tool that connects different sources or sinks toghether and via kafka. To use it, we need to define/use the connector that we want. it also has some predefined connectors that could be found in config directory of Kakfa.

 So let's dive into it!

to start a simple source Connector, first go to kafka installation directory and run:
```
bin/connect-standalone.sh config/connect-standalone.properties config/connect-file-source.properties
```
in `connect-file-source.properties`, `topic` and the source `file` name is specified, it's relative addressing. after this, any line added to this file will be passed to defined `topic`.

To check the payloads streamed via Connect, you can run this command:

```
bin/kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic connect-test
```
Also Kafka Connect has a rest api service that we can check/update/create/delete/pause the connectors. 

```
## check running connectors:
curl http://localhost:8083/connectors | python -m json.tool

## create new connector:
curl -X POST -H 'Content-Type: application/json' -d '{
>     "name": "first-connector",
>     "config": {
>         "connector.class": "FileStreamSource",
>         "tasks.max": 1,
>         "file": "/var/log/journal/confluent-kafka-connect.service.log",
>         "topic": "kafka-connect-logs"
>     }
>   }' \
>   http://localhost:8083/connectors

## delete a connector:
curl -X DELETE http://localhost:8083/connectors/first-connector

## check details of a connector:
curl http://localhost:8083/connectors/first-connector | python -m json.tool
```


-------
Useful links:

[learn basics of Kafka Connect](https://shravan-kuchkula.github.io/kafka-connect-stream-data-into-kafka/#list-existing-connectors)

[learn how to start kafka connect via command line](https://supergloo.com/kafka-connect/)