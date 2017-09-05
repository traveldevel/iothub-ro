# Install steps

1. Ubuntu x64 vms for "ambari-server" and "ambari-agent" (min 3 machines)

2. Configure Hadoop, Zookeper and Kafka cluster services

3. Install Kafka Manager on port 9000
   
   https://github.com/yahoo/kafka-manager
   
   With script from : https://packagecloud.io/spuder/kafka-manager/install and `apt-get install kafka-manager`
   
   
3. Install Node.js and front-end apps

   3.1. Node.js ingestion to hotstore and coldstore and event generation app
   
   3.2. Node.js API
   
   3.3. UI5 front end app
   
   3.4. Analytics app
