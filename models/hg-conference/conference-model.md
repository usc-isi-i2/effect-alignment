# conferenceCDR-extractions.jl

## Add Column

## Add Node/Literal

## PyTransforms
#### _timestamp_iso_
From column: _timestamp_
``` python
return DM.iso8601date(getValue("timestamp"))
```

#### _conference_uri_
From column: _json_rep / url_
``` python
return UM.uri_from_fields("conference/", getValue("url"))
```

#### _datePublsihedISO_
From column: _json_rep / timestamp_
``` python
date = getValue("timestamp").split('.')[0]
if len(date) > 0:
    return DM.iso8601date(date, "%Y-%m-%dT%H:%M:%S")
return ''
```

#### _cve_uri_
From column: _extractions / cve / result / value_
``` python
cve = getValue("value")
if len(cve) > 0:
   return "vulnerability/" + cve.upper()
```

#### _msid_uri_
From column: _extractions / msid / result / value_
``` python
x = getValue("value").strip()
if len(x) > 0:
   return "securityUpdate/" + x.upper()
```


## Selections

## Semantic Types
| Column | Property | Class |
|  ----- | -------- | ----- |
| __id_ | `schema:source`<BR> - _specified provenance_ | `memex:Conference1`|
| _conference_uri_ | `uri` | `memex:Conference1`|
| _cve_uri_ | `uri` | `memex:Vulnerability1`|
| _datePublsihedISO_ | `schema:startDate` | `memex:Conference1`|
| _meta_description_ | `schema:description` | `memex:Conference1`|
| _meta_keywords_ | `schema:keywords` | `memex:Conference1`|
| _msid_uri_ | `uri` | `memex:SecurityUpdate1`|
| _source_name_ | `schema:publisher`<BR> - _specified provenance_ | `memex:Conference1`|
| _text_ | `schema:text` | `memex:Conference1`|
| _timestamp_iso_ | `memex:dateRecorded`<BR> - _specified provenance_ | `memex:Conference1`|
| _title_ | `schema:name` | `memex:Conference1`|
| _url_ | `schema:url` | `memex:Conference1`|


## Links
| From | Property | To |
|  --- | -------- | ---|
| `memex:Conference1` | `memex:mentionsSecurityUpdate` | `memex:SecurityUpdate1`|
| `memex:Conference1` | `schema:mentions` | `memex:Vulnerability1`|
