## test.jl

### PyTransforms
#### _uri_
From column: __id_
``` python
return "event/" + getValue("_id")
```


### Semantic Types
| Column | Property | Class |
|  ----- | -------- | ----- |
| _attack_ | `memex:hasType` | `memex:AttackEvent1`|
| _author_ | `schema:name` | `memex:PersonOrOrganization1`|
| _date_ | `schema:startDate` | `memex:AttackEvent1`|
| _description_ | `schema:description` | `memex:AttackEvent1`|
| _link_ | `schema:source` | `memex:AttackEvent1`|
| _target_ | `schema:name` | `memex:PersonOrOrganization2`|
| _uri_ | `uri` | `memex:AttackEvent1`|


### Links
| From | Property | To |
|  --- | -------- | ---|
| `memex:AttackEvent1` | `memex:affected` | `memex:PersonOrOrganization2`|
| `memex:AttackEvent1` | `memex:owner` | `memex:PersonOrOrganization1`|
