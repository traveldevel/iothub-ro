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

#### Create the user provided services out of the 4 apps deployed on steps 8-11

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

#### Ingestion related apps and tasks :

16. Create a Kafka Server Broker Instance (see below chapter : Bitnami Kafka appliance - v0 - fastest)

17. Deploy ingestion app to Kafka :  `https://github.com/traveldevel/iot-hub-ingestion-rest`

18. Deploy Kafka topic consumer app for ingestion: `https://github.com/traveldevel/iot-hub-ingestion-processor`

19. Deploy Kafka topic consumer app for event processing : `https://github.com/traveldevel/iot-hub-event-processor`

####

20. API management with API Umbrela on the Ubuntu Kafka Host [here](https://api-umbrella.readthedocs.io/en/latest/getting-started.html#setup)


## Managed Kafka Service for free (with SSL only) : 

https://customer.cloudkarafka.com/instance/create?plan=ducky

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

if updated in the future : https://packagecloud.io/spuder/kafka-manager

## Install steps own Kafka - v1 - fast

https://www.digitalocean.com/community/tutorials/how-to-install-apache-kafka-on-ubuntu-14-04

Open ports : 2181, 9092, 2888, 3888

Install script from : https://packagecloud.io/spuder/kafka-manager/install and `apt-get install kafka-manager`

You may need to instal default jre : `sudo apt-get install default-jre`

Custom Start Command : `sudo kafka-manager -Dconfig.file=/etc/kafka-manager/application.conf -Dhttp.port=9001`

## Install steps own Kafka - v2 (bonus hadoop and ambari), slower

1. Ubuntu x64 - 14.04 LTS !!! vms for "ambari-server" and "ambari-agent" (min 3 machines)

   https://docs.hortonworks.com/HDPDocuments/Ambari-2.5.2.0/bk_ambari-installation/content/download_the_ambari_repo_ubuntu14.html
   
   https://cwiki.apache.org/confluence/display/AMBARI/Quick+Start+for+New+VM+Users#QuickStartforNewVMUsers-InstallAmbariontheVirtualMachines

   open ports : 3000, 6667, 6188, 8020, 8080, 8440, 8441, 8670, 9093, 9001
   
   edit `/etc/hostname`
   
   edit `/etc/hosts`
   
   Use full host name with domain when configurings cluster hosts

2. Configure Hadoop - HDP 2.4 !!!, Zookeper and Kafka cluster services

   Change the the "listeners" property from Kafka Broker to the PLAINTEXT://hostname:9093
   
   Change port to 9093
   
   Install Kafka Manager as a Docker container on port 9001 and run with 

   `docker run -it --rm  -p 9000:9001 -e ZK_HOSTS="172.16.43.128:2181" -e APPLICATION_SECRET=admin sheepkiller/kafka-manager`

  
## Other links : 
   
   https://github.com/yahoo/kafka-manager
   
   https://github.com/sheepkiller/kafka-manager-docker
   
## Create CF landscape apps front-end / backend / workers

   0. Establish : 
      * Name of the landscape
      * Name of the tenant
      * Create prerequired MongoDB service 
      * Deploy mongo-express Node.js app to administer MongoDB data
      * Deploy CF Node.js app that creates tenant
   
   1. Node.js API - data ingestion to kafka (REST)
   
   2. Node.js Worker - Data Ingestion Processing to Hot Store (Mongo)
   
   3. Node.js Express OData API on top of Mongo
   
   4. Node.js worker - Transfer to Coldstore and Event generate 
   
   5. Static files HTML5 app - UI5 front end app
   
   6. Analytics app with custom BI reporting tool
   
   
   Example node.js kafka apps : 
   
   https://github.com/SOHU-Co/kafka-node

   http://whatizee.blogspot.de/2015/02/nodejs-kafka-producer-using-kafka-node.html
   
## Local CF VM machine install script : https://github.com/pivotal-cf/pcfdev
