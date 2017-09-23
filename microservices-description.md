## Each LANDSCAPE in its own Cloud Foundry Space and Org

## Microservices in each landscape and for each tenant

  ### 0. Ingestion REST Microservice (iot-hub-ingestion-rest-LANDSCAPE-TENANT)
  
  
  ### 1. Metadata OData Service (iot-hub-metadata-odata-LANDSCAPE-TENANT)
  
  
  ### 2. Raw Data OData Service (iot-hub-rawdata-odata-LANDSCAPE-TENANT)
  
  
  ### 3. Rules, Events and Commands OData Service (named : iot-hub-event-odata-LANDSCAPE-TENANT)
  
  
  ### 4. Locations OData Service (named : iot-hub-location-odata-LANDSCAPE-TENANT) 


## MongoDB services or DBs in each landscape (common for all tenants)

  ### 1. MongoDB for Metadata (named :  iot_hub_mongo_metadata_LANDSCAPE_TENANT)
  
  ### 2. MongoDB for Raw Data (named :  iot_hub_mongo_rawdata_LANDSCAPE_TENANT)
  
  ### 3. MongoDB for Rules, Events and Commands (named : iot_hub_mongo_events_LANDSCAPE_TENANT)
  
  ### 4. MongoDB for Locations (named :  iot_hub_mongo_location_LANDSCAPE_TENANT) 
  
  
  * Note : LANDSCAPE, TENANT replaceable with real names 
