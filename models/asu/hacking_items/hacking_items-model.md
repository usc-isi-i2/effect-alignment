## HI_karma.jl

### PyTransforms
#### _item_id_
From column: _json_rep / itemId_
>``` python
return "item/"+getValue("itemId")
```

#### _vendor_id_
From column: _json_rep / vendorId_
>``` python
return "vendor_id/"+getValue("vendorId")
```

#### _marketplace_id_
From column: _json_rep / marketplaceId_
>``` python
return "marketplace/"+getValue("marketplaceId")
```

#### _posted_date_iso_
From column: _json_rep / postedDate_
>``` python
t =  getValue("postedDate")
return DM.iso8601date(t,"%m-%d-%Y")
```

#### _source_name_id_
From column: _source_name_
>``` python
return "source/"+getValue("source_name")
```

#### _cdr_id_
From column: __id_
>``` python
return "identifier/"+getValue("_id")
```


### Semantic Types
| Column | Property | Class |
|  ----- | -------- | ----- |
| _cdr_id_ | `uri` | `memex:Identifier1`|
| _clusterName_ | `memex:hasType` | `memex:SoftwareSystem1`|
| _itemCategory_ | `schema:category` | `memex:SoftwareSystem1`|
| _itemDescription_ | `schema:description` | `memex:SoftwareSystem1`|
| _itemName_ | `schema:name` | `memex:SoftwareSystem1`|
| _itemShippedFrom_ | `schema:name` | `schema:Place1`|
| _itemShippedTo_ | `schema:name` | `schema:Place2`|
| _itemVendorRating_ | `schema:ratingValue` | `memex:SoftwareSystem1`|
| _item_id_ | `uri` | `memex:SoftwareSystem1`|
| _marketplace_id_ | `uri` | `schema:Place3`|
| _source_name_id_ | `uri` | `memex:Identifier2`|
| _vendor_id_ | `uri` | `memex:PersonOrOrganization1`|


### Links
| From | Property | To |
|  --- | -------- | ---|
| `memex:Identifier1` | `memex:hasType` | `xsd:http://effect.isi.edu/identifier/database`|
| `memex:Identifier2` | `memex:hasType` | `xsd:http://effect.isi.edu/identifier/source`|
| `memex:SoftwareSystem1` | `memex:identifier` | `memex:Identifier1`|
| `memex:SoftwareSystem1` | `memex:identifier` | `memex:Identifier2`|
| `memex:SoftwareSystem1` | `schema:containedInPlace` | `schema:Place3`|
| `memex:SoftwareSystem1` | `schema:fromLocation` | `schema:Place1`|
| `memex:SoftwareSystem1` | `schema:seller` | `memex:PersonOrOrganization1`|
| `memex:SoftwareSystem1` | `schema:toLocation` | `schema:Place2`|
