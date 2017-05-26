# blogsCDR-extractions.jl

## Add Column

## Add Node/Literal

## PyTransforms
#### _link_uri_
From column: _json_rep / link_
``` python
return UM.uri_from_fields("blogs/", getValue("link"))
```

#### _datePublishedBestKnown_
From column: _json_rep / published_
``` python
x = getValue("published")
if len(x) > 0:
  return DM.iso8601date(x)
y = getValue("parsed")
if len(y) > 0:
  return DM.iso8601date(y)
return ''
```

#### _timestamp_iso_
From column: _timestamp_
``` python
return DM.iso8601date(getValue("timestamp"))
```

#### _cve_uri_
From column: _extractions / cve / result / value_
``` python
x= getValue("value")
if len(x) > 0:
  return "vulnerability/"+getValue("value").upper()
return ''
```

#### _blog_uri_
From column: _extractions / json_rep.text_
``` python
return getValueFromNestedColumnByIndex("json_rep", "link_uri", getRowIndex())
```

#### _extraction_uri_
From column: _extractions / json_rep.text / text_
``` python
x = getValue("text").strip()
blog_uri = getValue("blog_uri")
if len(x) > 0:
  x = re.sub('[^A-Za-z0-9]+', '', x)
  return blog_uri + "/extraction/" + getValue("label") + "/" + x
```


## Selections

## Semantic Types
| Column | Property | Class |
|  ----- | -------- | ----- |
| __id_ | `schema:source`<BR> - _specified provenance_ | `schema:Blog1`|
| _cve_uri_ | `uri` | `memex:Vulnerability1`|
| _datePublishedBestKnown_ | `schema:datePublished` | `schema:Blog1`|
| _extraction_uri_ | `uri` | `memex:Extraction1`|
| _extractor_ | `memex:extractor` | `memex:Extraction1`|
| _label_ | `memex:hasType` | `memex:Extraction1`|
| _link_ | `schema:url` | `schema:Blog1`|
| _link_uri_ | `uri` | `schema:Blog1`|
| _source_name_ | `schema:publisher`<BR> - _specified provenance_ | `schema:Blog1`|
| _text_ | `schema:text` | `memex:Extraction1`|
| _text_ | `schema:text` | `schema:Blog1`|
| _timestamp_iso_ | `memex:dateRecorded`<BR> - _specified provenance_ | `schema:Blog1`|
| _title_ | `schema:title` | `schema:Blog1`|


## Links
| From | Property | To |
|  --- | -------- | ---|
| `schema:Blog1` | `memex:hasExtraction` | `memex:Extraction1`|
| `schema:Blog1` | `schema:mentions` | `memex:Vulnerability1`|
