# iothub-ro

# Architecture Hierarchy

 - Landscapes (example : shared1)
 - Tenants (example : myaccount)
 - Projects (example : vehicle-tracking)
 - Device groups (example : buses)
 - Devices (DEVICE_ID is GUID)
 
# Implementation details

Landscape = each instance of the hub

Components of each Landscape :

  - Ingestion (raw data, events, locations) : Kafka topic + node.js app to handle each topic and raise events
  - Transfer to hotstore (Mongo DB) + Transfer to coldstore (if activated - Hadoop)
  - Hub UI Admin (ui5 app)
  - Hub UI Analytics (later on)
  - REST API for data and entities admin (node.js)
  
Conventions :

  - Landscape URI : http://<LANDSCAPE_NAME>.iothub.ro (example : http://shared1.iothub.ro)
  - Tenant URI : http://<LANDSCAPE_NAME>.iothub.ro/<TENANT_NAME> (example : http://shared1.iothub.ro/myaccount)
  - Project URI : http://<LANDSCAPE_NAME>.iothub.ro/<TENANT_NAME> (example : http://shared1.iothub.ro/myaccount/vehicle-tracking)
  - Group URI : http://<LANDSCAPE_NAME>.iothub.ro/<TENANT_NAME> (example : http://shared1.iothub.ro/myaccount/vehicle-tracking/buses)
  - Device URI : http://<LANDSCAPE_NAME>.iothub.ro/<TENANT_NAME> (example : http://shared1.iothub.ro/myaccount/vehicle-tracking/buses/<DEVICE_ID>)
  
  - Tenants has different Mongo DBs with name : <TENANT_NAME>_tenant
  - Tenants have different Hadoop folders and files : 
  
      /<LANDSCAPE_NAME>/<TENANT_NAME>/<PROJECT_GUID>/<GROUP_GUID>/<DEVICE_GUID>/rawdata.csv
      /<LANDSCAPE_NAME>/<TENANT_NAME>/<PROJECT_GUID>/<GROUP_GUID>/<DEVICE_GUID>/events.csv
      /<LANDSCAPE_NAME>/<TENANT_NAME>/<PROJECT_GUID>/<GROUP_GUID>/<DEVICE_GUID>/locations.csv
  
  - projects, groups, devices, locations, events, rawdata are entities stored in different tables 

# Fields for "projects"

- guid
- name
- description

# Fields for "groups"

- guid
- project (guid)
- name
- description

# Fields for "device_schemas"

- guid
- project (guid)
- name
- values ( key = type pair list)

# Fields for "devices"

- guid
- project (guid)
- group (guid)
- name
- authToken (another auto guid) 
- description
- createdAt (datetime)
- lastContact (datetime)
- validateSchema (if any : guid)

# Fields for "locations"

- guid
- project (guid)
- group (guid)
- device (guid)
- latitude (decimal)
- longitude (decimal)
- accuracy (int)
- speed (int)
- recordedTime (datetime)
- createdAt (datetime)

# Fields for "rawdata"

- guid
- project (guid)
- group (guid)
- device (guid)
- values ( key = value pair list)
- recordedTime (datetime)
- createdAt (datetime)

# Install steps

See here
