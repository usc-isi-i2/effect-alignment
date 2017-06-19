# hg_zdi-for-karma.jl

## Add Column

## Add Node/Literal

## PyTransforms
#### _cdr_id_
From column: _json_rep / zdi_id_
``` python
return "vulnerability/"+getValue("zdi_id").upper()
```

#### _cvss_scoring_
From column: _json_rep / cdr_id_
``` python
return "vulnerability/"+getValue("zdi_id").upper()+"/scoring"
```

#### _uri_id_
From column: __id_
``` python
return getValue("_id")
```

#### _source_name_id_
From column: _source_name_
``` python
return getValue("source_name")
```

#### _dateRecorded_iso_
From column: _timestamp_
``` python
return DM.iso8601date(getValue("timestamp"))
```

#### _software_uri_
From column: _json_rep / affected_products / values_
``` python
x = getValue("values").strip()
if len(x) > 0:
   return UM.uri_from_fields("software/", x) 
```

#### _date_iso_
From column: _json_rep / date_
``` python
return DM.iso8601date(getValue("date"))
```


## Selections

## Semantic Types
| Column | Property | Class |
|  ----- | -------- | ----- |
| _access_complexity_ | `memex:cvssComplexity` | `memex:CVSS1`|
| _access_vector_ | `memex:cvssAccessVector` | `memex:CVSS1`|
| _authentication_ | `memex:cvssAuthentication` | `memex:CVSS1`|
| _availability_impact_ | `memex:cvssAvailability` | `memex:CVSS1`|
| _cdr_id_ | `uri` | `memex:Vulnerability1`|
| _confidentiality_impact_ | `memex:cvssConfidentiality` | `memex:CVSS1`|
| _cvss_scoring_ | `uri` | `memex:CVSS1`|
| _dateRecorded_iso_ | `memex:dateRecorded`<BR> - _specified provenance_ | `memex:CVSS1`|
| _date_iso_ | `schema:startDate` | `memex:Vulnerability1`|
| _integrity_impact_ | `memex:cvssIntegrity` | `memex:CVSS1`|
| _link_ | `schema:url` | `memex:Vulnerability1`|
| _software_uri_ | `uri` | `memex:SoftwareSystem1`|
| _source_name_id_ | `schema:publisher`<BR> - _specified provenance_ | `memex:CVSS1`|
| _title_ | `schema:title` | `memex:Vulnerability1`|
| _uri_id_ | `schema:source`<BR> - _specified provenance_ | `memex:CVSS1`|
| _values_ | `schema:name` | `memex:SoftwareSystem1`|
| _values_ | `schema:seller` | `memex:SoftwareSystem1`|
| _values_ | `schema:sourcedFrom` | `memex:Vulnerability1`|
| _vulnerability_details_ | `schema:description` | `memex:Vulnerability1`|
| _zdi_id_ | `schema:name` | `memex:Vulnerability1`|


## Links
| From | Property | To |
|  --- | -------- | ---|
| `memex:Vulnerability1` | `memex:hasCVSS` | `memex:CVSS1`|
| `memex:Vulnerability1` | `memex:vulnerabilityOf` | `memex:SoftwareSystem1`|
