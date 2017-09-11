
# Fields for "<TENANT_NAME>_project"

- guid
- name
- description

# Fields for "<TENANT_NAME>_device_group"

- guid
- project (guid)
- name
- description

# Fields for "<TENANT_NAME>_device_schema"

- guid
- project (guid)
- name
- values ( key = type pair list)

# Fields for "<TENANT_NAME>_device"

- guid
- project (guid)
- group (guid)
- name
- authToken (another auto guid) 
- description
- createdAt (datetime)
- lastContact (datetime)
- validateSchema (if any : guid)

# Fields for "<TENANT_NAME>_location"

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

# Fields for "<TENANT_NAME>_rawdata"

- guid
- project (guid)
- group (guid)
- device (guid)
- values ( key = value pair list)
- recordedTime (datetime)
- createdAt (datetime)

# Fields for "<TENANT_NAME>_user"

- guid
- name
- password
- roles
