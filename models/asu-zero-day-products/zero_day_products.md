## ZDP_karma.jl

### PyTransforms
#### _item_id_
From column: _json_rep / itemId_
>``` python
return "item/"+getValue("itemId")
```

#### _posted_date_iso_
From column: _json_rep / postedDate_
>``` python
t =  getValue("postedDate")
return DM.iso8601date(t,"%d/%m/%Y")
 
```

#### _cdr_id_
From column: __id_
>``` python
return "identifier/"+getValue("_id")
```

#### _source_name_id_
From column: _source_name_
>``` python
return "source/"+getValue("source_name")
```


### Semantic Types
| Column | Property | Class |
|  ----- | -------- | ----- |
| _cdr_id_ | `uri` | `memex:Identifier1`|
| _clusterName_ | `memex:hasType` | `memex:SoftwareSystem1`|
| _description_ | `schema:description` | `memex:SoftwareSystem1`|
| _itemName_ | `schema:name` | `memex:SoftwareSystem1`|
| _item_id_ | `uri` | `memex:SoftwareSystem1`|
| _posted_date_iso_ | `schema:datePosted` | `memex:SoftwareSystem1`|
| _sellingPriceUsd_ | `schema:price` | `memex:SoftwareSystem1`|
| _source_name_id_ | `uri` | `memex:Identifier2`|


### Links
| From | Property | To |
|  --- | -------- | ---|
| `memex:Identifier1` | `memex:hasType` | `xsd:http://effect.isi.edu/identifier/database`|
| `memex:Identifier2` | `memex:hasType` | `xsd:http://effect.isi.edu/identifier/source`|
| `memex:SoftwareSystem1` | `memex:identifier` | `memex:Identifier1`|
| `memex:SoftwareSystem1` | `memex:identifier` | `memex:Identifier2`|
