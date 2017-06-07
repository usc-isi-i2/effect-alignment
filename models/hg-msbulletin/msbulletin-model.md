# msbulletinCDR-extractions.jl

## Add Column

## Add Node/Literal

## PyTransforms
#### _cve_uri_
From column: _extractions / cve / result / value_
``` python
return "vulnerability/"+ getValue("value").upper()
```

#### _id_clean_
From column: _json_rep / id_
``` python
return getValue("id").upper()
```

#### _update_uri_
From column: _json_rep / id_clean_
``` python
x = getValue("id_clean")
if len(x) > 0:
   return "securityUpdate/" + x
```

#### _published_iso_
From column: _json_rep / published_
``` python
return DM.iso8601date(getValue("published"))
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
| __id_ | `schema:source`<BR> - _specified provenance_ | `memex:SecurityUpdate1`|
| _cve_uri_ | `uri` | `memex:Vulnerability1`|
| _id_clean_ | `schema:name` | `memex:SecurityUpdate1`|
| _published_iso_ | `schema:datePublished` | `memex:SecurityUpdate1`|
| _source_name_ | `schema:publisher`<BR> - _specified provenance_ | `memex:SecurityUpdate1`|
| _text_ | `schema:text` | `memex:SecurityUpdate1`|
| _timestamp_iso_ | `memex:dateRecorded`<BR> - _specified provenance_ | `memex:SecurityUpdate1`|
| _title_ | `schema:title` | `memex:SecurityUpdate1`|
| _update_uri_ | `uri` | `memex:SecurityUpdate1`|


## Links
| From | Property | To |
|  --- | -------- | ---|
| `memex:SecurityUpdate1` | `memex:fixesVulnerability` | `memex:Vulnerability1`|
| `memex:Vulnerability1` | `memex:isFixedBy` | `memex:SecurityUpdate1`|
