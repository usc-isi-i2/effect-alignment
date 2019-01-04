# unc-phish-alerts-CDR.jl

## Add Column

## Add Node/Literal
#### Node: `schema:EmailMessage1`
Uri: `http://schema.org/EmailMessage`
<br/>Id: `http://schema.org/EmailMessage1`

#### Node: `memex:PersonOrOrganization1`
Uri: `http://schema.dig.isi.edu/ontology/PersonOrOrganization`
<br/>Id: `http://schema.dig.isi.edu/ontology/PersonOrOrganization1`


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
| _body_ | `schema:text` | `schema:EmailMessage1`|
| _sender_ | `uri` | `memex:EmailAddress1`|
| _source_name_ | `schema:publisher` | `schema:EmailMessage1`|
| _timestamp_ | `schema:datePublished` | `schema:EmailMessage1`|
| _timestamp_iso_ | `memex:dateRecorded` | `schema:EmailMessage1`|
| _title_ | `schema:title` | `schema:EmailMessage1`|


## Links
| From | Property | To |
|  --- | -------- | ---|
| `memex:PersonOrOrganization1` | `schema:email` | `memex:EmailAddress1`|
| `schema:EmailMessage1` | `schema:actor` | `memex:PersonOrOrganization1`|
