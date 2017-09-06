
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
