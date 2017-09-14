
## Fields for "tenants"

- _id
- tenant_name
- tenant_secret (guid)

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
- description
- values ( key = type pair list)

## Fields for "<TENANT_NAME>_device"

- _id
- project_id (_id)
- device_group_id (_id)
- device_name
- auth_token (auto _id) 
- description
- created_at (datetime)
- last_contact (datetime)
- mandatory_schema_id (_id)
- validate_schema (if any : _id)

## Fields for "<TENANT_NAME>_location"

- _id
- project_id (_id)
- group_id (_id)
- device_id (_id)
- latitude (decimal)
- longitude (decimal)
- accuracy (int)
- speed (int)
- recorded_time (datetime)
- created_at (datetime)

## Fields for "<TENANT_NAME>_raw_data"

- _id
- project_id (_id)
- group_id (_id)
- device_group_id (_id)
- device_id (_id)
- values ( key = value pair list)
- recorded_time (datetime)
- created_at (datetime)

## Fields for "<TENANT_NAME>_event"

To Do

## Fields for "<TENANT_NAME>_command"

To Do

## Fields for "<TENANT_NAME>_user"

- _id
- name
- password
- roles
