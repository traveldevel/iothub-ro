# iothub-ro

# Architecture Hierarchy

 - Landscapes (example : shared1)
 - Tenants (example : myaccount)
 - Projects (example : vehicle-tracking)
 - Device groups (example : buses)
 - Devices
 
# Implementation details

Landscape = each instance of the hub

Components of each Landscape :

  - Ingestion (raw data, events, locations) : Kafka topic + Node.Js API to handle each topic and raise events
  - Transfer to hotstore (Mongo DB) + Transfer to coldstore (if activated - Hadoop)
  - Hub UI Admin
  - Hub UI Analytics
  
Conventions :

  - Landscape URI : http://<LANDSCAPE>.iothub.ro (example : http://shared1.iothub.ro)
  - Tenant URI : http://<LANDSCAPE>.iothub.ro/<TENANT_NAME> (example : http://shared1.iothub.ro/myaccount)
  - Project URI : http://<LANDSCAPE>.iothub.ro/<TENANT_NAME> (example : http://shared1.iothub.ro/myaccount/vehicle-tracking)
  - Group URI : http://<LANDSCAPE>.iothub.ro/<TENANT_NAME> (example : http://shared1.iothub.ro/myaccount/vehicle-tracking/buses)
  - Device URI : http://<LANDSCAPE>.iothub.ro/<TENANT_NAME> (example : http://shared1.iothub.ro/myaccount/vehicle-tracking/buses/<DEVICE_ID>)
  
  - Tenants has different Mongo DBs with name : <TENANT_NAME>_tenant
  - Tenants have different Hadoop folders and files : 
  
      /<LANDSCAPE>/<TENANT_NAME>/<PROJECT>/<GROUP>/<DEVICE>/rawdata.csv
      /<LANDSCAPE>/<TENANT_NAME>/<PROJECT>/<GROUP>/<DEVICE>/events.csv
      /<LANDSCAPE>/<TENANT_NAME>/<PROJECT>/<GROUP>/<DEVICE>/locations.csv
  
  - projects, groups, devices, locations, events, rawdata are entities stored in different tables 
 
# Install steps

See here
