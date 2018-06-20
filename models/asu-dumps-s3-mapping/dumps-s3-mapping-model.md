# dumps-s3-mapping-cdr.jl

## Add Column

## Add Node/Literal
#### Literal Node: `CodeDump`
Literal Type: ``
<br/>Language: ``
<br/>isUri: `false`


## PyTransforms
#### _malware_uri_
From column: _json_rep / id_
``` python
x = getValue("id")
if len(x) > 0:
    return "malware/" +x 
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
| _fileName_ | `memex:fileName` | `memex:Malware1`|
| _id_ | `memex:contentMD5` | `memex:Malware1`|
| _languageType_ | `schema:programmingLanguage` | `memex:Malware1`|
| _malware_uri_ | `uri` | `memex:Malware1`|
| _sha256Hash_ | `memex:contentSHA256` | `memex:Malware1`|
| _source_name_ | `schema:publisher`<BR> - _specified provenance_ | `memex:Malware1`|
| _timestamp_iso_ | `memex:dateRecorded`<BR> - _specified provenance_ | `memex:Malware1`|


## Links
| From | Property | To |
|  --- | -------- | ---|
| `memex:Malware1` | `memex:hasType` | `CodeDump`|
