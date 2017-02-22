# hgAbuseChCDR.jl

## Add Column

## Add Node/Literal

## PyTransforms
#### _timestamp_iso_
From column: _timestamp_
``` python
return DM.iso8601date(getValue("timestamp"))
```

#### _first_seen_iso_
From column: _json_rep / first_seen_
``` python
return DM.iso8601date(getValue("first_seen"), "%Y-%m-%dT%H:%M:%SZ")
```

#### _url_hash_
From column: _json_rep / url_
``` python
return  "malware/" + SM.md5_hash(getValue("url"))

```

#### _ip_address_uri_
From column: _json_rep / associated_ip_stats / ip_address_
``` python
x = getValue("ip_address")
if x:
   x = SM.alpha_numeric(x).replace(" ","_")
   return "ipaddress/" + x
return ''
```

#### _firstseen_iso_
From column: _json_rep / associated_ip_stats / firstseen_
``` python
return DM.iso8601date(getValue("firstseen"), "%Y-%m-%dT%H:%M:%SZ")
```


## Selections

## Semantic Types
| Column | Property | Class |
|  ----- | -------- | ----- |
| __id_ | `schema:source` | `memex:Malware1`|
| _as_name_ | `memex:autonomousSystemName` | `memex:IPAddress1`|
| _as_number_ | `memex:autonomousSystemNumber` | `memex:IPAddress1`|
| _country_ | `schema:countryOfOrigin` | `memex:IPAddress1`|
| _country_ | `schema:countryOfOrigin` | `memex:Malware1`|
| _first_seen_iso_ | `memex:observedDate` | `memex:Malware1`|
| _firstseen_iso_ | `memex:observedDate` | `memex:IPAddress1`|
| _ip_address_ | `schema:name` | `memex:IPAddress1`|
| _ip_address_uri_ | `uri` | `memex:IPAddress1`|
| _malware_ | `schema:name` | `memex:Malware1`|
| _md5_ | `memex:nameMD5` | `memex:Malware1`|
| _registrar_ | `memex:registrar` | `memex:IPAddress1`|
| _sha256_ | `memex:nameSHA1` | `memex:Malware1`|
| _source_name_ | `schema:publisher` | `memex:Malware1`|
| _timestamp_iso_ | `memex:dateRecorded` | `memex:Malware1`|
| _url_ | `schema:url` | `memex:Malware1`|
| _url_hash_ | `uri` | `memex:Malware1`|


## Links
| From | Property | To |
|  --- | -------- | ---|
| `memex:Malware1` | `memex:hostedAt` | `memex:IPAddress1`|
