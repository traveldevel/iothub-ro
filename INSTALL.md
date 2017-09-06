# Install steps

1. Ubuntu x64 vms for "ambari-server" and "ambari-agent" (min 3 machines)

2. Configure Hadoop, Zookeper and Kafka cluster services

   Change the the "listeners" property from Kafka Borker to the Hostname/IP

3. Install Kafka Manager as a Docker container on port 9000 and run with 

   `docker run -it --rm  -p 9000:9000 -e ZK_HOSTS="172.16.43.128:2181" -e APPLICATION_SECRET=admin sheepkiller/kafka-manager`

   Other Links : 
   
   https://github.com/yahoo/kafka-manager
   
   https://github.com/sheepkiller/kafka-manager-docker
   
   Install script from : https://packagecloud.io/spuder/kafka-manager/install and `apt-get install kafka-manager`
   
   Custom Start Command : `kafka-manager -Dconfig.file=/etc/kafka-manager/application.conf -Dhttp.port=9001`
   
3. Install Node.js and front-end apps

   3.1. Node.js ingestion to hotstore and coldstore and event generation app
   
   3.2. Node.js API
   
   3.3. UI5 front end app
   
   3.4. Analytics app
   
   Example node.js kafka apps : 
   
   https://github.com/SOHU-Co/kafka-node

   http://whatizee.blogspot.de/2015/02/nodejs-kafka-producer-using-kafka-node.html
   
4. Local CF VM machine install script : https://github.com/pivotal-cf/pcfdev
