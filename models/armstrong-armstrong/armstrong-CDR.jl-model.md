# armstrong-CDR.jl

## Add Column

## Add Node/Literal

## PyTransforms
#### _dateRecorded_
From column: _timestamp_
``` python
return DM.iso8601date(getValue("timestamp"), "%Y-%m-%d %H:%M:%S.%f")
```


## Selections

## Semantic Types
| Column | Property | Class |
|  ----- | -------- | ----- |
| _COUNT_ | `memex:count` | `memex:Exploit1`|
| _DATE_ | `schema:datePublished` | `memex:Exploit1`|
| _TYPE_ | `memex:hasType` | `memex:Exploit1`|
| __id_ | `uri` | `memex:Exploit1`|
| _dateRecorded_ | `memex:dateRecorded` | `memex:Exploit1`|
| _source_name_ | `schema:publisher` | `memex:Exploit1`|


## Links
| From | Property | To |
|  --- | -------- | ---|
