# Scalable data ingestion from device


  - <PROJECT_ID>_device_raw_data - where the device will write messages by it's own or thru the REST API
    
  - <PROJECT_ID>_to_cold_store - forwarded messages for transfer to cold store after beeing saved to hot store, if enabled
  
  - <PROJECT_ID>_to_event_processing - forwarded messages for rule/events processing to cold store after beeing saved to hot store, if enabled

1. Node.js CF REST API as backend (optional) that writes data to <PROJECT_ID>_device_raw_data topic

2. Node.Js app that will read the <PROJECT_ID>_to_cold_store topic save messages to cold store

3. Node.Js app that will read the <PROJECT_ID>_to_event_processing topic and check with the rules engine for events if functionalities are enabled
