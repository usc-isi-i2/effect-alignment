# hgCPECDR.jl

## Add Column

## Add Node/Literal

## PyTransforms
#### _timestamp_iso_
From column: _timestamp_
``` python
return DM.iso8601date(getValue("timestamp"), "%Y-%m-%d %H:%M:%S.%f")
```


## Selections

## Semantic Types
| Column | Property | Class |
|  ----- | -------- | ----- |
| __id_ | `schema:source` | `memex:SoftwareSystem1`|
| _cpe_23_name_ | `uri` | `memex:SoftwareSystem1`|
| _language_ | `schema:language` | `memex:SoftwareSystem1`|
| _product_ | `schema:name` | `memex:SoftwareSystem1`|
| _source_name_ | `schema:publisher` | `memex:SoftwareSystem1`|
| _timestamp_iso_ | `memex:dateRecorded` | `memex:SoftwareSystem1`|
| _title_ | `schema:title` | `memex:SoftwareSystem1`|
| _vendor_ | `schema:vendor` | `memex:SoftwareSystem1`|
| _version_ | `schema:version` | `memex:SoftwareSystem1`|


## Links
| From | Property | To |
|  --- | -------- | ---|
