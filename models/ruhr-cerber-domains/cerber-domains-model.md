# cerber-domains-for-karma.jl

## Add Column

## Add Node/Literal
#### Node: `memex:Malware1`
Uri: `http://schema.dig.isi.edu/ontology/Malware`
<br/>Id: `http://schema.dig.isi.edu/ontology/Malware1`

#### Literal Node: `Cerber`
Literal Type: `xsd:string`
<br/>Language: ``
<br/>isUri: `false`


## PyTransforms
#### _date_iso_
From column: _json_rep / date_
``` python
x = getValue("date")
return DM.iso8601date(x)
```

#### _timestamp_iso_
From column: _timestamp_
``` python
return DM.iso8601date(getValue("timestamp"))
```

#### _malware_url_
From column: _json_rep / domain_
``` python
x = getValue("domain").strip()
if len(x) > 0:
  return "http://" + x
return ''
```

#### _malware_url_hash_
From column: _json_rep / malware_url_
``` python
x = getValue("malware_url")
if len(x) > 0:
  return  "malware/" + SM.md5_hash(x)

```


## Selections

## Semantic Types
| Column | Property | Class |
|  ----- | -------- | ----- |
| __id_ | `schema:source`<BR> - _specified provenance_ | `memex:Malware1`|
| _date_iso_ | `memex:observedDate` | `memex:Malware1`|
| _malware_url_ | `schema:url` | `memex:Malware1`|
| _malware_url_hash_ | `uri` | `memex:Malware1`|
| _source_name_ | `schema:publisher`<BR> - _specified provenance_ | `memex:Malware1`|
| _timestamp_iso_ | `memex:dateRecorded`<BR> - _specified provenance_ | `memex:Malware1`|


## Links
| From | Property | To |
|  --- | -------- | ---|
| `memex:Malware1` | `schema:name` | `Cerber`|
