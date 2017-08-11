# company-cpe-cdr.jl

## Add Column

## Add Node/Literal

## PyTransforms
#### _cpe_prefix_uri_
From column: _json_rep / cpe_prefix_
``` python
x = getValue("cpe_prefix")
if len(x) > 0:
   return "cpe:/" + x
```

#### _prefix_name_
From column: _json_rep / cpe_prefix_uri_
``` python
return getValue("cpe_prefix_uri")
```

#### _company_uri_
From column: _json_rep / company_
``` python
x = getValue("company")
if len(x) > 0:
   return UM.uri_from_fields("organization/", x)
```

#### _timestamp_iso_
From column: _timestamp_
``` python
return DM.iso8601date(getValue("timestamp"))
```

#### _values_lower_
From column: _json_rep / mentions / values_
``` python
return getValue("values").lower()
```

#### _mentions_uri_
From column: _json_rep / mentions / values_lower_
``` python
return getValue("company_uri") + UM.uri_from_fields("/extraction/", getValue("values_lower"))
```


## Selections

## Semantic Types
| Column | Property | Class |
|  ----- | -------- | ----- |
| __id_ | `schema:source`<BR> - _specified provenance_ | `memex:Extraction1`|
| _company_ | `schema:name` | `schema:Organization1`|
| _company_uri_ | `uri` | `schema:Organization1`|
| _cpe_prefix_uri_ | `uri` | `memex:SoftwareSystemClass1`|
| _mentions_uri_ | `uri` | `memex:Extraction1`|
| _prefix_name_ | `memex:hasType` | `memex:Extraction1`|
| _prefix_name_ | `schema:name` | `memex:SoftwareSystemClass1`|
| _source_name_ | `schema:publisher`<BR> - _specified provenance_ | `memex:Extraction1`|
| _source_name_ | `memex:extractor` | `memex:Extraction1`|
| _timestamp_iso_ | `memex:dateRecorded`<BR> - _specified provenance_ | `memex:Extraction1`|
| _values_lower_ | `schema:text` | `memex:Extraction1`|


## Links
| From | Property | To |
|  --- | -------- | ---|
| `memex:SoftwareSystemClass1` | `memex:softwareIsUsedIn` | `schema:Organization1`|
| `schema:Organization1` | `memex:usesSoftware` | `memex:SoftwareSystemClass1`|
| `schema:Organization1` | `memex:hasExtraction` | `memex:Extraction1`|
