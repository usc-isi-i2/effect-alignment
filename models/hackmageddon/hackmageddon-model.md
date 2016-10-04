## hackmageddon-py-script.jl

### PyTransforms
#### _cdr_id_
From column: __id_
>``` python
return "event/"+getValue("_id")
```

#### _author_clean_
From column: _json_rep / author_
>``` python
a = getValue("author")
return a.replace('?','')
```

#### _country_clean_
From column: _json_rep / country_
>``` python
t = getValue("country")
if t[0].isalnum() == False:
    return ''
else:
    return t
```

#### _date_iso_
From column: _json_rep / date_
>``` python
t =  getValue("date")
return DM.iso8601date(t,"%d/%m/%Y")
```

#### _target_name_cleaned_
From column: _json_rep / target_
>``` python
t = getValue("target")
if t[0].isalnum() == False:
    return ''
else:
    return t
```

#### _target_class_cleaned_
From column: _json_rep / target_class_
>``` python
t = getValue("target_class")
if t[0].isalnum() == False:
    return ''
else:
    return t
```


### Semantic Types
| Column | Property | Class |
|  ----- | -------- | ----- |
| _Values_ | `schema:keywords` | `memex:AttackEvent1`|
| _attack_ | `memex:hasType` | `memex:AttackEvent1`|
| _attack_class_ | `schema:additionalType` | `memex:AttackEvent1`|
| _author_clean_ | `schema:name` | `memex:PersonOrOrganization1`|
| _cdr_id_ | `uri` | `memex:AttackEvent1`|
| _country_clean_ | `schema:name` | `schema:Place1`|
| _date_iso_ | `schema:startDate` | `memex:AttackEvent1`|
| _description_ | `schema:description` | `memex:AttackEvent1`|
| _link_ | `schema:url` | `memex:AttackEvent1`|
| _target_class_cleaned_ | `schema:subtype` | `memex:PersonOrOrganization2`|
| _target_name_cleaned_ | `schema:name` | `memex:PersonOrOrganization2`|


### Links
| From | Property | To |
|  --- | -------- | ---|
| `memex:AttackEvent1` | `memex:affected` | `memex:PersonOrOrganization2`|
| `memex:AttackEvent1` | `schema:actor` | `memex:PersonOrOrganization1`|
| `memex:AttackEvent1` | `schema:location` | `schema:Place1`|
