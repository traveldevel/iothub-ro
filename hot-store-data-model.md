
# Hot Store - Mongo DB - dbs / CF services

Administered with one `mongo-express` CF app instance

## 1.  Metadata (named : iot_hub_mongo_LANDSCAPE_TENANT_metadata)

Used for all the metadata models and used by the metadata service.

### Fields for "tenants"

- _id
- tenant_name
- tenant_secret (guid)
- tenant_hdfs_coldstore (bool)
- tenant_rule_processing (bool)

### Fields for "TENANT_user"

- _id
- name
- password
- roles

### Fields for "TENANT_project"

- _id
- project_name
- description

### Fields for "TENANT_device_group"

- _id
- project (_id)
- group_name
- description

### Fields for "TENANT_device_schema"

- _id
- project (_id)
- schema_name
- description
- values ( key = type pair list)

### Fields for "TENANT_device"

- _id
- project_id (_id)
- group_id (_id)
- device_name
- auth_token (auto _id) 
- description
- created_at (datetime)
- last_contact_ping (datetime)
- last_contact_rawdata (datetime)
- last_contact_location (datetime)
- last_event_triggered (datetime)
- last_command_sent (datetime)
- last_command_confirmed (datetime)
- mandatory_schema_id (_id)
- validate_schema (bool)
- trigger_events (bool)
- archive_to_coldstore (bool)

## 2.  Raw Data (iot_hub_mongo_LANDSCAPE_TENANT_rawdata)

### Fields for "TENANT_raw_data"

- _id
- project_id (_id)
- group_id (_id)
- device_id (_id)
- values ( key = value pair list)
- recorded_time (datetime)
- created_at (datetime)

## 3.  Rules, Events and Commands (iot_hub_mongo_LANDSCAPE_TENANT_event)

### Fields for "TENANT_event"

- _id
- project_id (_id)
- group_id (_id)
- device_id (_id)
- type
- text
- dismissed (bool)
- user_id (_id)
- rule_id
- rawdata_id
- triggered_at

### Fields for "TENANT_event_rule"

- _id
- device_id (_id) - optional, if present : device rule
- group_id (_id) - optional, if present : group rule
- project_id (_id) - optional, if present : project_rule
- rule_name
- operator (eq, ne, gt, le, in)
- operator_reference (as string)

Obs : all rules apply (project, group and device)

### Fields for "TENANT_command"

- _id
- project_id (_id)
- group_id (_id)
- device_id (_id)
- type
- command
- created_at (datetime)
- confirmed_at (datetime)

## 4.  Locations (iot_hub_mongo_LANDSCAPE_TENANT_location)

### Fields for "TENANT_location"

- _id
- project_id (_id)
- group_id (_id)
- device_id (_id)
- latitude (decimal)
- longitude (decimal)
- accuracy (int)
- speed (decimal)
- elevation (int)
- heading (string)
- recorded_time (datetime)
- created_at (datetime)
