# APACHE-KAFKA-SPRINGBOOT-MICROSERVICES
We have created 2 springboot consumer and producer.

Commands to run Kafka on CLS

Start zookeeper
bin\windows\zookeeper-server-start.bat config\zookeeper.properties

Without zookeeper with latest version (Not needed this step when zookeeper running)
// UUID generated in powersell using -> [guid]::NewGuid()
//3be90423-83ca-4628-8430-916ec37bc90e
bin\windows\kafka-storage.bat format --standalone -t d08103ca-d2c3-4234-a4fb-97b1d93b5c25 -c config\server.properties


Start Kafka server
bin\windows\kafka-server-start.bat config\server.properties

Create topic 
bin\windows\kafka-topics.bat --create --topic pnr-topic --bootstrap-server localhost:9092

Create producer
bin\windows\kafka-console-producer.bat --topic pnr-topic --bootstrap-server localhost:9092

Create consumer
bin\windows\kafka-console-consumer.bat --topic pnr-topic --bootstrap-server localhost:9092
bin\windows\kafka-console-consumer.bat --topic location-update-topic --from-beginning --bootstrap-server localhost:9092



Update config\server.properties  if you face errors for configuration (only applicable for latest versions 4.0.0)
-------------------------------------
# ------------------------------
# Kafka 4.0.0 Single-node KRaft
# ------------------------------

# Node & process roles
process.roles=broker,controller
node.id=1

# Controller quorum voters (node.id@host:port)
controller.quorum.voters=1@localhost:9093

# Listeners
listeners=PLAINTEXT://localhost:9092,CONTROLLER://localhost:9093
controller.listener.names=CONTROLLER
inter.broker.listener.name=PLAINTEXT

# Data directories (Windows-friendly)
log.dirs=.\kafka-logs
metadata.log.dir=.\kafka-metadata-logs

# Internal topics - single node = replication factor 1
offsets.topic.replication.factor=1
transaction.state.log.replication.factor=1
transaction.state.log.min.isr=1
default.replication.factor=1
min.insync.replicas=1

# Misc
num.partitions=1
-------------------------------------
