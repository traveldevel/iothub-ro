# Scalable data ingestion from device

Each LANSCAPE has its own Kafka Instance

## Kafka Topics (for each Project specific to a Tenant of a Landscape)

1. KAFKA_TOPIC_PREFIX-LANDSCAPE-TENANT-raw-data (data sent to a Node.js REST api)

2. KAFKA_TOPIC_PREFIX-LANDSCAPE-TENANT-for-event-rules (data sent to a Node.js REST api - if events processing is active then check rules and create events)

3. KAFKA_TOPIC_PREFIX-LANDSCAPE-TENANT-for-coldstore-history (data sent to a Node.js REST api - if coldstore history enabled then transfer to coldstore)

All topics with only 1 partition : partition 0 !

## REST API and Worker Apps involved in data ingestion

1. Node.js CF REST API as backend (optional) that writes data to <PROJECT_ID>_device_raw_data topic

2. Node.Js worker app that reads the KAFKA_TOPIC_PREFIX-LANDSCAPE-TENANT-raw-data topic save messages to cold store

3. Node.Js worker app that reads the KAFKA_TOPIC_PREFIX-LANDSCAPE-TENANT-for-event-rules topic and check with the rules engine for events if functionalities are enabled

4. Node.Js worker app that reads the KAFKA_TOPIC_PREFIX-LANDSCAPE-TENANT-for-coldstore-history topic and transfer raw data to coldstore
