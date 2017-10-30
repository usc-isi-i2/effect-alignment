# hackingitemsCDR-extractions.jl

## Add Column

## Add Node/Literal
#### Literal Node: `USD`
Literal Type: ``
<br/>Language: ``
<br/>isUri: `false`


## PyTransforms
#### _marketplace_id_
From column: _json_rep / marketplaceId_
``` python
x = getValue("marketplaceId")
if len(x) > 0:
  return "marketplace/"+ x
x = getValue("marketPlaceId")
if len(x) > 0:
   return "marketplace/"+ x
```

#### _vendor_id_
From column: _json_rep / uid_
``` python
return getValue("marketplace_id") + "/vendor_id/"+getValue("uid")
```

#### _item_id_
From column: _json_rep / itemId_
``` python
return getValue("marketplace_id") + "/exploit/"+getValue("itemId")
```

#### _posted_date_iso_
From column: _json_rep / postedDate_
``` python
t =  getValue("postedDate")
return DM.iso8601date(t,"%m-%d-%Y")
```

#### _source_name_id_
From column: _source_name_
``` python
return getValue("source_name")
```

#### _cdr_id_
From column: __id_
``` python
return getValue("_id")
```

#### _price_uri_
From column: _json_rep / sellingPriceUsd_
``` python
return "price/" + getValue("sellingPriceUsd") + "USD"
```

#### _fromplace_uri_
From column: _json_rep / itemShippedFrom_
``` python
return UM.uri_from_fields("place/", getValue("itemShippedFrom"))
```

#### _toPlace_uri_
From column: _json_rep / itemShippedTo_
``` python
return UM.uri_from_fields("place/", getValue("itemShippedTo"))
```

#### _dateRecorded_
From column: _timestamp_
``` python
return DM.iso8601date(getValue("timestamp"), "%Y-%m-%d %H:%M:%S.%f")
```

#### _cve_uri_
From column: _extractions / cve / result / value_
``` python
x = getValue("value").strip()
if len(x) > 0:
  return "vulnerability/" + x.upper()
```

#### _msid_uri_
From column: _extractions / msid / result / value_
``` python
x = getValue("value").strip()
if len(x) > 0:
   return "securityUpdate/" + x.upper()
```

#### _recordedDateTimeISO_
From column: _json_rep / recordedTime_
``` python
rt = getValue("recordedDate") + "T" + getValue("recordedTime")
if len(rt) > 0:
   return DM.iso8601date(rt)
return ''
```


## Selections

## Semantic Types
| Column | Property | Class |
|  ----- | -------- | ----- |
| _cdr_id_ | `schema:source`<BR> - _specified provenance_ | `memex:Exploit1`|
| _cve_uri_ | `uri` | `memex:Vulnerability1`|
| _dateRecorded_ | `memex:dateRecorded`<BR> - _specified provenance_ | `memex:PersonOrOrganization1`|
| _fromplace_uri_ | `uri` | `schema:Place1`|
| _itemCategory_ | `schema:category` | `memex:Exploit1`|
| _itemDescription_ | `schema:description` | `memex:Exploit1`|
| _itemName_ | `schema:name` | `memex:Exploit1`|
| _itemShippedFrom_ | `schema:name` | `schema:Place1`|
| _itemShippedTo_ | `schema:name` | `schema:Place2`|
| _itemVendorRating_ | `schema:ratingValue` | `memex:PersonOrOrganization1`|
| _item_id_ | `uri` | `memex:Exploit1`|
| _marketplace_id_ | `uri` | `memex:PersonOrOrganization2`|
| _msid_uri_ | `uri` | `memex:SecurityUpdate1`|
| _price_uri_ | `uri` | `schema:PriceSpecification1`|
| _recordedDateTimeISO_ | `schema:datePosted` | `memex:Exploit1`|
| _sellingPriceUsd_ | `schema:price` | `schema:PriceSpecification1`|
| _source_name_id_ | `schema:publisher`<BR> - _specified provenance_ | `memex:Exploit1`|
| _toPlace_uri_ | `uri` | `schema:Place2`|
| _values_ | `memex:financialTags` | `memex:Exploit1`|
| _values_ | `memex:softwareTags` | `memex:Exploit1`|
| _values_ | `schema:keywords` | `memex:Exploit1`|
| _vendor_id_ | `uri` | `memex:PersonOrOrganization1`|


## Links
| From | Property | To |
|  --- | -------- | ---|
| `memex:Exploit1` | `memex:mentionsSecurityUpdate` | `memex:SecurityUpdate1`|
| `memex:Exploit1` | `schema:priceSpecification` | `schema:PriceSpecification1`|
| `memex:Exploit1` | `schema:toLocation` | `schema:Place2`|
| `memex:Exploit1` | `schema:fromLocation` | `schema:Place1`|
| `memex:Exploit1` | `memex:exploitsVulnerability` | `memex:Vulnerability1`|
| `memex:Exploit1` | `schema:seller` | `memex:PersonOrOrganization2`|
| `memex:Exploit1` | `schema:vendor` | `memex:PersonOrOrganization1`|
| `memex:Vulnerability1` | `memex:hasExploit` | `memex:Exploit1`|
| `schema:PriceSpecification1` | `schema:priceCurrency` | `USD`|
