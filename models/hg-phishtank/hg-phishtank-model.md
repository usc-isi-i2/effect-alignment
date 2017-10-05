# phishtank-cdr.jl

## Add Column

## Add Node/Literal
#### Literal Node: `Phish`
Literal Type: ``
<br/>Language: ``
<br/>isUri: `false`


## PyTransforms
#### _ip_address_uri_
From column: _json_rep / details / ip_address_
``` python
x = getValue("ip_address")
if len(x) > 0:
    return "ipaddress/" + x
```

#### _phish_uri_
From column: _json_rep / phish_id_
``` python
return "malware/phishank/" + getValue("phish_id")
```

#### _detail_time_iso_
From column: _json_rep / details / detail_time_
``` python
return DM.iso8601date(getValue("detail_time"),"%Y-%m-%dT%H:%M:%S%Z")
```

#### _reported_by_name_
From column: _json_rep / phish_detail_url_
``` python
x = getValue("phish_detail_url")
if len(x) > 0:
  i = x.find("://")
  start = 0
  if i !- -1:
     start = i+3
  i = x.find("/", start)
  if i != -1:
     x = x[0:i+1]
  return x
```

#### _reported_by_uri_
From column: _json_rep / reported_by_name_
``` python
x = getValue("reported_by_name")
if len(x) > 0:
   return "organization/" + SM.fingerprint_string(x)
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
| __id_ | `schema:source`<BR> - _specified provenance_ | `memex:Malware1`|
| _country_ | `schema:countryOfOrigin` | `memex:Malware1`|
| _detail_time_iso_ | `memex:observedDate` | `memex:Malware1`|
| _ip_address_ | `schema:name` | `memex:IPAddress1`|
| _ip_address_uri_ | `uri` | `memex:IPAddress1`|
| _phish_uri_ | `uri` | `memex:Malware1`|
| _reported_by_name_ | `schema:name` | `memex:PersonOrOrganization1`|
| _reported_by_uri_ | `uri` | `memex:PersonOrOrganization1`|
| _source_name_ | `schema:publisher`<BR> - _specified provenance_ | `memex:Malware1`|
| _target_ | `schema:targetName` | `memex:Malware1`|
| _timestamp_iso_ | `memex:dateRecorded`<BR> - _specified provenance_ | `memex:Malware1`|
| _url_ | `schema:url` | `memex:Malware1`|


## Links
| From | Property | To |
|  --- | -------- | ---|
| `memex:Malware1` | `memex:hasType` | `Phish`|
| `memex:Malware1` | `memex:reportedBy` | `memex:PersonOrOrganization1`|
| `memex:Malware1` | `memex:hostedAt` | `memex:IPAddress1`|
