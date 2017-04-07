# taxiiCDR.jl

## Add Column

## Add Node/Literal

## PyTransforms
#### _timestamp_iso_
From column: _timestamp_
``` python
return DM.iso8601date(getValue("timestamp"))
```

#### _domain_
From column: _json_rep / observable / OR / title_
``` python
x = getValue("title")
if x.startswith("Domain:"):
  domain = x[7:].strip()
  if not domain.startswith("http"):
    domain = "http://" + domain
  return domain
return ''
```

#### _ip_uri_
From column: _json_rep / observable / value_
``` python
x = getValue("title")
if x.startswith("IP:"):
   return "ipaddress/" + x[3:].strip()
```

#### _obseved_timestamp_
From column: _json_rep / ttps / timestamp_
``` python
return DM.iso8601date(getValue("timestamp"))
```

#### _malware_uri_
From column: _json_rep / ttps / id_
``` python
x = getValue("id")
if len(x) > 0:
   return UM.uri_from_fields("malware/", x)

```

#### _producer_uri_
From column: _json_rep / producer_
``` python
x = getValue("producer")
if len(x) > 0:
   return "organization/" + SM.fingerprint_string(x)
```

#### _domain_url_
From column: _json_rep / observable / ip_uri_
``` python
x = getValue("title")
if x.startswith("Domain:"):
  domain = x[7:].strip()
  if not domain.startswith("http"):
    domain = "http://" + domain
  return domain
```


## Selections

## Semantic Types
| Column | Property | Class |
|  ----- | -------- | ----- |
| __id_ | `schema:source`<BR> - _specified provenance_ | `memex:Malware1`|
| _behavior_name_ | `schema:name` | `memex:Malware1`|
| _behavior_type_ | `memex:hasType` | `memex:Malware1`|
| _description_ | `schema:description` | `memex:Malware1`|
| _domain_ | `schema:url` | `memex:Malware1`|
| _domain_url_ | `schema:url` | `memex:Malware1`|
| _ip_uri_ | `uri` | `memex:IPAddress1`|
| _malware_uri_ | `uri` | `memex:Malware1`|
| _obseved_timestamp_ | `memex:observedDate` | `memex:Malware1`|
| _producer_ | `schema:name` | `memex:PersonOrOrganization1`|
| _producer_uri_ | `uri` | `memex:PersonOrOrganization1`|
| _source_name_ | `schema:publisher`<BR> - _specified provenance_ | `memex:Malware1`|
| _target_name_ | `schema:targetName` | `memex:Malware1`|
| _timestamp_iso_ | `memex:dateRecorded`<BR> - _specified provenance_ | `memex:Malware1`|
| _value_ | `schema:name` | `memex:IPAddress1`|


## Links
| From | Property | To |
|  --- | -------- | ---|
| `memex:Malware1` | `memex:hostedAt` | `memex:IPAddress1`|
| `memex:Malware1` | `memex:reportedBy` | `memex:PersonOrOrganization1`|
