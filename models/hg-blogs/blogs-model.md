# blogsCDR.jl

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


## Selections

## Semantic Types
| Column | Property | Class |
|  ----- | -------- | ----- |
| __id_ | `schema:source` | `schema:Blog1`|
| _datePublishedBestKnown_ | `schema:datePublished` | `schema:Blog1`|
| _link_ | `schema:url` | `schema:Blog1`|
| _link_uri_ | `uri` | `schema:Blog1`|
| _source_name_ | `schema:publisher` | `schema:Blog1`|
| _text_ | `schema:text` | `schema:Blog1`|
| _timestamp_iso_ | `memex:dateRecorded` | `schema:Blog1`|
| _title_ | `schema:title` | `schema:Blog1`|


## Links
| From | Property | To |
|  --- | -------- | ---|
