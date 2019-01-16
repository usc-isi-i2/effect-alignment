# armstrong-CDR.jl

## Add Column

## Add Node/Literal
#### Node: `schema:EmailMessage1`
Uri: `http://schema.org/EmailMessage`
<br/>Id: `http://schema.org/EmailMessage1`


## PyTransforms
#### _timestamp_iso_
From column: _timestamp_
``` python
return DM.iso8601date(getValue("timestamp"))
```

#### _temps_threats_
From column: _json_rep / threatsInfoMap_
``` python
import json
threats_info =  json.loads(getValue("threatsInfoMap"))
threat_type = threats_info[0]['threatType']
if not isinstance(threat_type, list):
    threat_type = [threat_type]
return json.dumps(threat_type)
```


## Selections

## Semantic Types
| Column | Property | Class |
|  ----- | -------- | ----- |
| _GUID_ | `uri` | `schema:EmailMessage1`|
| _messageTime_ | `schema:datePublished` | `schema:EmailMessage1`|
| _source_name_ | `schema:publisher` | `schema:EmailMessage1`|
| _subject_ | `schema:title` | `schema:EmailMessage1`|
| _threatType_ | `memex:hasType` | `schema:EmailMessage1`|
| _timestamp_iso_ | `memex:dateRecorded` | `schema:EmailMessage1`|


## Links
| From | Property | To |
|  --- | -------- | ---|
