# taxiiCDR.jl

## Add Column

## Add Node/Literal

## PyTransforms
#### _ip2_
From column: _json_rep / observable / OR / title_
``` python
x = getValue("title")
if x.startswith("IP:"):
  ip = x[4:].strip()
  return ip
return ''
```

#### _domain2_
From column: _json_rep / observable / OR / title_
``` python
x = getValue("title")
domain = ''
if x.startswith("Domain:"):
  domain = x[7:].strip()
elif x.startswith("URL:"):
  domain = x[4:].strip()
if len(domain) > 0:
  if not domain.startswith("http"):
    domain = "http://" + domain
  return domain
```

#### _ip_addr_
From column: _json_rep / observable / title_
``` python
x = getValue("title")
if x.startswith("IP:"):
   return x[3:].strip()
x = getValueFromNestedColumnByIndex("observable", "OR/ip2", getRowIndex())
return x
```

#### _domain_
From column: _json_rep / observable / ip_addr_
``` python
x = getValue("title")
result = ''
if x.startswith("Domain:"):
   result = x[7:].strip()
elif x.startswith("URL:"):
   result = x[4:].strip()
if len(result) == 0:
   result = getValueFromNestedColumnByIndex("observable", "OR/domain2", getRowIndex())
if len(result) > 0:
   if not result.startswith("http"):
       result = "http://" + result
else:
    ip = getValue("ip_addr")
    if len(ip) > 0:
       result = "http://" + ip
return result
```

#### _ip_uri_
From column: _json_rep / observable / ip_addr_
``` python
x = getValue("ip_addr")
if len(x) > 0:
    return "ipaddress" + x
```

#### _dateRecorded_
From column: _timestamp_
``` python
return DM.iso8601date(getValue("timestamp"))
```

#### _observed_timestamp_
From column: _json_rep / ttps / timestamp_
``` python
return DM.iso8601date(getValue("timestamp"))
```

#### _malware_uri_
From column: _json_rep / ttps / id_
``` python
x = getValue("id")
if len(x) > 0:
   domain_url = getValueFromNestedColumnByIndex("observable", "domain", getRowIndex())
   return UM.uri_from_fields("malware/", x, domain_url)

```

#### _producer_uri_
From column: _json_rep / producer_
``` python
x = getValue("producer")
if len(x) > 0:
   return "organization/" + SM.fingerprint_string(x)
```


## Selections

## Semantic Types
| Column | Property | Class |
|  ----- | -------- | ----- |
| __id_ | `schema:source`<BR> - _specified provenance_ | `memex:Malware1`|
| _behavior_name_ | `schema:name` | `memex:Malware1`|
| _behavior_type_ | `memex:hasType` | `memex:Malware1`|
| _dateRecorded_ | `memex:dateRecorded`<BR> - _specified provenance_ | `memex:Malware1`|
| _description_ | `schema:description` | `memex:Malware1`|
| _domain_ | `schema:url` | `memex:Malware1`|
| _ip_addr_ | `schema:name` | `memex:IPAddress1`|
| _ip_uri_ | `uri` | `memex:IPAddress1`|
| _malware_uri_ | `uri` | `memex:Malware1`|
| _observed_timestamp_ | `memex:observedDate` | `memex:Malware1`|
| _producer_ | `schema:name` | `memex:PersonOrOrganization1`|
| _producer_uri_ | `uri` | `memex:PersonOrOrganization1`|
| _source_name_ | `schema:publisher`<BR> - _specified provenance_ | `memex:Malware1`|
| _target_name_ | `schema:targetName` | `memex:Malware1`|


## Links
| From | Property | To |
|  --- | -------- | ---|
| `memex:Malware1` | `memex:reportedBy` | `memex:PersonOrOrganization1`|
| `memex:Malware1` | `memex:hostedAt` | `memex:IPAddress1`|
