## Cloud Foundry TENANT install ops (developed and tested on https://run.pivotal.io/)

#### Initial tenant steps :

0. Create org : `iot_hub_LANDSCAPE`
1. Create space : `iot_hub_TENANT`

2. Create MongoDb service : `iot_hub_mongo_shared_new_metadata`
3. Create MongoDb service : `iot_hub_mongo_shared_new_rawdata`
4. Create MongoDb service : `iot_hub_mongo_shared_new_location`
5. Create MongoDb service : `iot_hub_mongo_shared_new_event`
6. Check the newly created MongoDB database indexes on each collection to be present

7. Deploy app : `https://github.com/traveldevel/iot-hub-create-tenant`

Get from users collection the first user (admin) and it's password and use it as CF env var for folowing 4 app deployes (in the .env file)

#### Backend Odata Services (as microservices architecture)

8. Deploy app : `https://github.com/traveldevel/iot-hub-service-odata-metadata`
9. Deploy app : `https://github.com/traveldevel/iot-hub-service-odata-rawdata`
10. Deploy app : `https://github.com/traveldevel/iot-hub-service-odata-location`
11. Deploy app : `https://github.com/traveldevel/iot-hub-service-odata-event`
12. Deploy app : `https://github.com/traveldevel/iot-hub-service-files`

#### Create the user provided services out of the 4 apps deployed on steps 8-12

Parameters :
- url : url of the app that processes the request (after deployment)
- user : user for basic auth on each app
- password : password for basic auth on each app

12. Create User provided service for metadata :
`cf cups iot-hub-service-odata-shared-new-metadata -p "url,user,password"`

13. Create User provided service for rawdata :
`cf cups iot-hub-service-odata-shared-new-rawdata -p "url,user,password"`

14. Create User provided service for location :
`cf cups iot-hub-service-odata-shared-new-location -p "url,user,password"`

15. Create User provided service for event :
`cf cups iot-hub-service-odata-shared-new-event -p "url,user,password"`

16. Create User provided service for files :
`cf cups iot-hub-service-shared-new-files -p "url,user,password"`

#### Ingestion related apps and tasks :

17. Create a Kafka Server Broker Instance (see below chapter : Bitnami Kafka appliance - v0 - fastest)

18. Deploy ingestion app to Kafka :  `https://github.com/traveldevel/iot-hub-ingestion-rest`

19. Deploy Kafka topic consumer app for ingestion: `https://github.com/traveldevel/iot-hub-ingestion-processor`

20. Deploy Kafka topic consumer app for event processing : `https://github.com/traveldevel/iot-hub-event-processor`

#### API Management and tracing for : metadata, event, location, rawdata, ingestion

21. API management with API Umbrela on the Ubuntu Linux that hosts Kafka Host [here](https://api-umbrella.readthedocs.io/en/latest/getting-started.html#setup). 

22. Configure the first admin user on https://hostname/admin 

23. Publish the 6 apis to API Umbrella and test their functionality with a new Api Key / User. For each API in general settings forward the Basxi auth user and password created in metadata service , user collection

## Bitnami Kafka appliance - v0 - fastest

https://docs.bitnami.com/virtual-machine/infrastructure/kafka/

http://www.scala-sbt.org/release/docs/Installing-sbt-on-Linux.html

http://chennaihug.org/knowledgebase/yahoo-kafka-manager/

Edit your Kafka configuration file `/opt/bitnami/kafka/config/server.properties`

```
delete.topic.enable=true
auto.create.topics.enable=true
...
advertised.listeners=PLAINTEXT://iothubkafkashared.westeurope.cloudapp.azure.com:9092
advertised.host.name=iothubkafkashared.westeurope.cloudapp.azure.com
```

If updated in the future : https://packagecloud.io/spuder/kafka-manager

## Ambari Hadoop HDFS install

1. Ubuntu Server 16.04 LTS virtual machine
2. Set DNS hostname (static IP)
3. Edit `/etc/hosts` with the public IP and full host and domain name
4. Open ports for VM : 8080, 8020, 9000, 3000, 2181, 6188, 50075, 50010, 50070, 50090, 50470, 61310
5. Install Ambari and configure cluster : https://docs.hortonworks.com/HDPDocuments/Ambari-2.5.2.0/bk_ambari-installation/content/download_the_ambari_repo_ubuntu16.html

## Azure Hortonworks Sandbox VM instance

0. Open ports : 8080, 4200, 8888
1. edit admin password : http://HOST:4200/ (intial : root / hadoop)
2. http://HOST:8080/ - Ambari
3. http://HOST:8888/ - Ambari


