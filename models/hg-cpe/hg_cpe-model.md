# hgCPECDR.jl

## Add Column

## Add Node/Literal

## PyTransforms
#### _timestamp_iso_
From column: _timestamp_
``` python
return DM.iso8601date(getValue("timestamp"), "%Y-%m-%d %H:%M:%S.%f")
```

#### _target_hardware_clean_
From column: _json_rep / cpe / target_hardware_
``` python
x = getValue("target_harware")
if x == "*":
    return ''
return x
```

#### _target_hardware_id_
From column: _json_rep / cpe / target_hardware_
``` python
x = getValue("target_hardware_clean")
if len(x) > 0:
   return "computerHardware/" + x
return ''
```

#### _target_software_clean_
From column: _json_rep / cpe / target_software_
``` python
x = getValue("target_software")
if x == "*":
  return ''
return x
```

#### _target_software_id_
From column: _json_rep / cpe / target_software_
``` python
x = getValue("target_software_clean")
if len(x) > 0:
   return "softwareSystem/" + x
return ''
```

#### _modification_date_iso_
From column: _json_rep / modification_date_
``` python
return DM.iso8601date(getValue("modification_date"))
```

#### _cpe_prefix_
From column: _json_rep / item_name_
``` python
cpe = getValue("item_name").strip()
if len(cpe) > 0:
  first_colon = cpe.find(":", 8)
  if first_colon != -1:
    second_colon = cpe.find(":", first_colon+1)
    if second_colon != -1:
        return cpe[0:second_colon]
```


## Selections

## Semantic Types
| Column | Property | Class |
|  ----- | -------- | ----- |
| __id_ | `schema:source`<BR> - _specified provenance_ | `memex:SoftwareSystem1`|
| _cpe_23_name_ | `schema:productID` | `memex:SoftwareSystem1`|
| _cpe_prefix_ | `uri` | `memex:SoftwareSystemClass1`|
| _item_name_ | `uri` | `memex:SoftwareSystem1`|
| _language_ | `schema:language` | `memex:SoftwareSystem1`|
| _modification_date_iso_ | `schema:dateModified` | `memex:SoftwareSystem1`|
| _product_ | `schema:name` | `memex:SoftwareSystem1`|
| _source_name_ | `schema:publisher`<BR> - _specified provenance_ | `memex:SoftwareSystem1`|
| _target_hardware_clean_ | `schema:name` | `memex:ComputerHardware1`|
| _target_hardware_id_ | `uri` | `memex:ComputerHardware1`|
| _target_software_clean_ | `schema:name` | `memex:SoftwareSystem2`|
| _target_software_id_ | `uri` | `memex:SoftwareSystem2`|
| _timestamp_iso_ | `memex:dateRecorded`<BR> - _specified provenance_ | `memex:SoftwareSystem1`|
| _title_ | `schema:title` | `memex:SoftwareSystem1`|
| _vendor_ | `schema:vendor` | `memex:SoftwareSystem1`|
| _version_ | `schema:version` | `memex:SoftwareSystem1`|


## Links
| From | Property | To |
|  --- | -------- | ---|
| `memex:SoftwareSystem1` | `memex:hasSoftwareClass` | `memex:SoftwareSystemClass1`|
| `memex:SoftwareSystem1` | `memex:targetSoftware` | `memex:SoftwareSystem2`|
| `memex:SoftwareSystem1` | `memex:platform` | `memex:ComputerHardware1`|
| `memex:SoftwareSystemClass1` | `memex:includesSoftwares` | `memex:SoftwareSystem1`|
