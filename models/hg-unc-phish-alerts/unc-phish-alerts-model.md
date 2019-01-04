# unc-phish-alerts-CDR.jl

## Add Column

## Add Node/Literal
#### Node: `schema:Blog1`
Uri: `http://schema.org/Blog`
<br/>Id: `http://schema.org/Blog1`


## PyTransforms
#### _timestamp_iso_
From column: _timestamp_
``` python
return DM.iso8601date(getValue("timestamp"))
```


## Selections

## Semantic Types
| Column | Property | Class |
|  ----- | -------- | ----- |
| _body_ | `schema:text` | `schema:Blog1`|
| _sender_ | `schema:url` | `schema:Blog1`|
| _source_name_ | `schema:publisher` | `schema:Blog1`|
| _timestamp_ | `schema:datePublished` | `schema:Blog1`|
| _timestamp_iso_ | `memex:dateRecorded` | `schema:Blog1`|
| _title_ | `schema:title` | `schema:Blog1`|


## Links
| From | Property | To |
|  --- | -------- | ---|
| `memex:PersonOrOrganization1` | `schema:email` | `memex:EmailAddress1`|
