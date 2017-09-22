## Managed Kafka Service for free (with SSL only) : 

https://customer.cloudkarafka.com/instance/create?plan=ducky

## Install steps own Kafka - v1 - fastest

https://www.digitalocean.com/community/tutorials/how-to-install-apache-kafka-on-ubuntu-14-04

Install script from : https://packagecloud.io/spuder/kafka-manager/install and `apt-get install kafka-manager`

You may need to instal default jre : `sudo apt-get install default-jre`

Custom Start Command : `sudo kafka-manager -Dconfig.file=/etc/kafka-manager/application.conf -Dhttp.port=9001`

## Install steps own Kafka - v2 (bonus hadoop and ambari)

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
