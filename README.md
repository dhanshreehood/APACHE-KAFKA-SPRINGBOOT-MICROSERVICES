# APACHE-KAFKA-SPRINGBOOT-MICROSERVICES
Kafka Spring Boot Microservices Project

This project demonstrates how to integrate Apache Kafka with Spring Boot Microservices for real-time data streaming and event-driven architecture. We have created 2 springboot consumer and producer.

🚀 Tech Stack
Java: 21
Spring Boot: 2.x / 3.x (depending on your setup)
Apache Kafka: 4.0.0-2.13 (KRaft mode, no Zookeeper required)
Build Tool: Maven
IDE: IntelliJ IDEA
API Testing Tool: Bruno

📦 Prerequisites
Make sure you have installed the following:
Java 21
Apache Kafka (I have used 4.0.0-2.13)
IntelliJ IDEA
Bruno (for API testing)
Git (optional, for version control)

⚙️ Setup Instructions
1️⃣ Clone the Repository
git clone https://github.com/your-username/APACHE-KAFKA-SPRINGBOOT-MICROSERVICES.git
cd APACHE-KAFKA-SPRINGBOOT-MICROSERVICES

2️⃣ Start Kafka (Windows - Command Line)
Option A: With Zookeeper (legacy mode, not required in v4.0.0)
# Start Zookeeper
bin\windows\zookeeper-server-start.bat config\zookeeper.properties

Option B: Without Zookeeper (KRaft mode – default in Kafka 4.0.0)
Format Storage Directory (one-time setup)
# Generate UUID
[guid]::NewGuid()

# Example UUID: 3be90423-83ca-4628-8430-916ec37bc90e

# Format storage
bin\windows\kafka-storage.bat format --standalone -t <generated-uuid> -c config\server.properties

Start Kafka Broker
bin\windows\kafka-server-start.bat config\server.properties

3️⃣ Build and Run Spring Boot Microservices
Open the project in IntelliJ IDEA and build it:
Project structure-> choose "SDK" and "Language level" your using
Right click on project-> Maven-> Sync Project

4️⃣ Test Using Bruno
Open Bruno.
Test: http://localhost:8080/location/latest

🛠️ Notes
Kafka 4.0.0 uses KRaft mode → Zookeeper is not needed.
UUID for storage formatting must be generated once before the first run.
If you restart Kafka frequently, storage formatting is not required again.
