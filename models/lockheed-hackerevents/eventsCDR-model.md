# hackerNewsCDR.jl

## Add Column

## Add Node/Literal

## PyTransforms
#### _event_id_
From column: _json_rep / Event ID_
``` python
return "event/" + getValue("Event ID")
```

#### _story_date_
From column: _json_rep / Story Date_
``` python
t = getValue("Story Date")
return DM.iso8601date(t,"%Y-%m-%d")
```


## Selections

## Semantic Types
| Column | Property | Class |
|  ----- | -------- | ----- |
| _Event Text_ | `schema:name` | `schema:Event1`|
| _Publisher_ | `schema:name` | `memex:PersonOrOrganization1`|
| _Sentence_ | `schema:description` | `schema:CreativeWork1`|
| _Target Name_ | `schema:name` | `memex:PersonOrOrganization2`|
| __id_ | `schema:source` | `schema:Event1`|
| _event_id_ | `uri` | `schema:Event1`|
| _source_name_ | `schema:publisher` | `schema:Event1`|
| _story_date_ | `schema:datePublished` | `schema:CreativeWork1`|


## Links
| From | Property | To |
|  --- | -------- | ---|
| `schema:CreativeWork1` | `schema:publisher` | `memex:PersonOrOrganization1`|
| `schema:Event1` | `memex:affected` | `memex:PersonOrOrganization2`|
| `schema:Event1` | `memex:isMentionedIn` | `schema:CreativeWork1`|
