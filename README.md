# iothub-ro

Install steps for each landscape : [here](INSTALL.md)

# Architecture Details

## Main semantic elements : 

 - Landscapes (example : shared)
 - Tenants (example : new)
 - Projects (example : vehicle-tracking)
 - Device groups (example : phones)
 - Devices

## Topic Detailed :

[Data Ingestion Processing Overview](https://github.com/traveldevel/iothub-ro/blob/master/data-ingestion-processing.md)

[Services Overview](https://github.com/traveldevel/iothub-ro/blob/master/microservices-description.md)

[Hot Data Store Model Descriptions](https://github.com/traveldevel/iothub-ro/blob/master/hot-store-data-model.md)

[TO DO : Cold Data Store Transfer Algoritm](https://github.com/traveldevel/iothub-ro/blob/master/cold-store-transfer-algorithm.md)

# Technologies Used

* Data Ingestion - Node.js REST API -> Kafka Broker

* Hot Store - Mongo DB (TO DO in version 0.1)

* Backend APIs for front end - Node.js OData (TO DO in version 0.1)

* Cold Store - Hadoop HDFS (TO DO in version 0.2)

* Event Processing - Node.js app that checks (TO DO in version 0.3)

* Frontend web app - OpenUI5 (TO DO in version 0.4)
