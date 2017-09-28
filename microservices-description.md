### Deployment description

- Each LANDSCAPE in its own adn different Cloud Foundry Org
- Each TENANT in its own different Cloud Foundry Space

- [Backend Architecture](https://github.com/traveldevel/iothub-ro/raw/master/images/IMG_20170928_100350.jpg)
- [Frontend Architecture](https://github.com/traveldevel/iothub-ro/raw/master/images/IMG_20170927_173626.jpg)

[How to Create a Node.js MongoDB OData Service](https://www.codeproject.com/Articles/1111490/Create-OData-endpoint-for-MongoDB-on-MEAN-stack)

### Microservices in each landscape and for each tenant

  * Ingestion REST Microservice (iot-hub-ingestion-rest-LANDSCAPE-TENANT)
  * Metadata OData Service (iot-hub-metadata-odata-LANDSCAPE-TENANT)
  * Raw Data OData Service (iot-hub-rawdata-odata-LANDSCAPE-TENANT)
  * Rules, Events and Commands OData Service (named : iot-hub-event-odata-LANDSCAPE-TENANT)
  * Locations OData Service (named : iot-hub-location-odata-LANDSCAPE-TENANT) 


### MongoDB services or DBs in each landscape and for each tenant

  * MongoDB for Metadata (named :  iot_hub_mongo_metadata_LANDSCAPE_TENANT)
  * MongoDB for Raw Data (named :  iot_hub_mongo_rawdata_LANDSCAPE_TENANT)
  * MongoDB for Rules, Events and Commands (named : iot_hub_mongo_events_LANDSCAPE_TENANT)
  * MongoDB for Locations (named :  iot_hub_mongo_location_LANDSCAPE_TENANT) 
  
  Note : LANDSCAPE, TENANT replaceable with real names 
