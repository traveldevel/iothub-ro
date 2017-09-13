
## Fields for "tenants_list"

- _id
- tenant_name

## Fields for "<TENANT_NAME>_project"

- _id
- project_name
- description

## Fields for "<TENANT_NAME>_device_group"

- _id
- project (_id)
- group_name
- description

## Fields for "<TENANT_NAME>_device_schema"

- _id
- project (_id)
- schema_name
- values ( key = type pair list)

## Fields for "<TENANT_NAME>_device"

- _id
- project (_id)
- device_group (_id)
- device_name
- authToken (auto _id) 
- description
- createdAt (datetime)
- lastContact (datetime)
- validateSchema (if any : _id)

## Fields for "<TENANT_NAME>_location"

- _id
- project (_id)
- group (_id)
- device (_id)
- latitude (decimal)
- longitude (decimal)
- accuracy (int)
- speed (int)
- recordedTime (datetime)
- createdAt (datetime)

## Fields for "<TENANT_NAME>_raw_data"

- _id
- project (_id)
- group (_id)
- device_group (_id)
- device (_id)
- values ( key = value pair list)
- recordedTime (datetime)
- createdAt (datetime)

## Fields for "<TENANT_NAME>_event"

To Do

## Fields for "<TENANT_NAME>_command"

To Do

## Fields for "<TENANT_NAME>_user"

- _id
- name
- password
- roles
