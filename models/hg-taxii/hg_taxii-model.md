# taxiiCDR.jl

## Add Column

## Add Node/Literal

## PyTransforms
#### _iso_timestamp_2_
From column: _json_rep / ttps / timestamp_
``` python

return DM.iso8601date(getValue("timestamp"))
```

#### _domain_url_
From column: _json_rep / observable / OR / description_
``` python
temp =  getValue("description")

if 'Domain' in temp:
    return temp.split('|')[0][7:]
```

#### _file_hash_value_
From column: _json_rep / observable / OR / description_
``` python
temp =  getValue("description")

if 'FileHash' in temp:
    return temp.split('|')[1][11:]
```

#### _nameMD5_
From column: _json_rep / observable / OR / hash_type_
``` python
if getValue("hash_type") == "MD5":
    return getValue("file_hash_value")
```

#### _nameSHA_
From column: _json_rep / observable / OR / hash_type_
``` python
if getValue("hash_type") == "SHA":
    return getValue("file_hash_value")
```

#### _ip_addr_uri_
From column: _json_rep / observable / value_
``` python
if getValue("value") != "":
    return "ipaddress/"+getValue("value")
```

#### _producer_uri_
From column: _json_rep / producer_
``` python
x = getValue("producer")
if x != '':
    return "organization/"+SM.fingerprint_string(x)
return x
```

#### _iso_timestamp_
From column: _json_rep / timestamp_
``` python
return DM.iso8601date(getValue("timestamp"))
```

#### _malware_uri_
From column: _json_rep / ttps / id_
``` python
return UM.uri_from_fields("malware/", getValue("id"))
```

#### _timestamp_iso_
From column: _timestamp_
``` python
return DM.iso8601date(getValue("timestamp"))
```


## Selections

## Semantic Types
| Column | Property | Class |
|  ----- | -------- | ----- |
| __id_ | `schema:source`<BR> - _specified provenance_ | `memex:IPAddress1`|
| _behavior_name_ | `schema:name` | `memex:Malware1`|
| _behavior_type_ | `memex:hasType` | `memex:Malware1`|
| _description_ | `schema:description` | `memex:Malware1`|
| _domain_url_ | `schema:url` | `memex:Malware1`|
| _ip_addr_uri_ | `uri` | `memex:IPAddress1`|
| _iso_timestamp_2_ | `memex:observedDate` | `memex:Malware1`|
| _malware_uri_ | `uri` | `memex:Malware1`|
| _nameMD5_ | `memex:nameMD5` | `memex:Malware1`|
| _producer_ | `schema:name` | `memex:PersonOrOrganization1`|
| _producer_uri_ | `uri` | `memex:PersonOrOrganization1`|
| _source_name_ | `schema:publisher`<BR> - _specified provenance_ | `memex:Malware1`|
| _target_name_ | `schema:targetName` | `memex:Malware1`|
| _timestamp_iso_ | `memex:dateRecorded`<BR> - _specified provenance_ | `memex:IPAddress1`|
| _title_ | `schema:title` | `memex:Malware1`|
| _value_ | `schema:name` | `memex:IPAddress1`|


## Links
| From | Property | To |
|  --- | -------- | ---|
| `memex:Malware1` | `memex:hostedAt` | `memex:IPAddress1`|
| `memex:Malware1` | `memex:reportedBy` | `memex:PersonOrOrganization1`|
