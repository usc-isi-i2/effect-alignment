# hgCPECDR.jl

## Add Column

## Add Node/Literal

## PyTransforms
#### _timestamp_iso_
From column: _timestamp_
``` python
return DM.iso8601date(getValue("timestamp"), "%Y-%m-%d %H:%M:%S.%f")
```

#### _target_hardware_id_
From column: _json_rep / cpe / target_hardware_
``` python
x = getValue("target_hardware_clean")
if len(x) > 0:
   return "/computerhardware/" + x
return ''
```

#### _target_software_id_
From column: _json_rep / cpe / target_software_
``` python
x = getValue("target_software_clean")
if len(x) > 0:
   return "/softwareSystem/" + x
return ''
```

#### _target_hardware_clean_
From column: _json_rep / cpe / target_hardware_
``` python
x = getValue("target_harware")
if x == "*":
    return ''
return x
```

#### _target_software_clean_
From column: _json_rep / cpe / target_software_
``` python
x = getValue("target_software")
if x == "*":
  return ''
return x
```


## Selections

## Semantic Types
| Column | Property | Class |
|  ----- | -------- | ----- |
| __id_ | `schema:source` | `memex:SoftwareSystem1`|
| __id_ | `schema:source` | `memex:SoftwareSystem2`|
| __id_ | `schema:source` | `memex:ComputerHardware1`|
| _item_name_ | `uri` | `memex:SoftwareSystem1`|
| _language_ | `schema:language` | `memex:SoftwareSystem1`|
| _product_ | `schema:name` | `memex:SoftwareSystem1`|
| _source_name_ | `schema:publisher` | `memex:SoftwareSystem1`|
| _source_name_ | `schema:publisher` | `memex:SoftwareSystem2`|
| _source_name_ | `schema:publisher` | `memex:ComputerHardware1`|
| _target_hardware_clean_ | `schema:name` | `memex:ComputerHardware1`|
| _target_hardware_id_ | `uri` | `memex:ComputerHardware1`|
| _target_software_clean_ | `schema:name` | `memex:SoftwareSystem2`|
| _target_software_id_ | `uri` | `memex:SoftwareSystem2`|
| _timestamp_iso_ | `memex:dateRecorded` | `memex:SoftwareSystem1`|
| _timestamp_iso_ | `memex:dateRecorded` | `memex:SoftwareSystem2`|
| _timestamp_iso_ | `memex:dateRecorded` | `memex:ComputerHardware1`|
| _title_ | `schema:title` | `memex:SoftwareSystem1`|
| _vendor_ | `schema:vendor` | `memex:SoftwareSystem1`|
| _version_ | `schema:version` | `memex:SoftwareSystem1`|


## Links
| From | Property | To |
|  --- | -------- | ---|
| `memex:SoftwareSystem1` | `memex:platform` | `memex:ComputerHardware1`|
| `memex:SoftwareSystem1` | `memex:targetSoftware` | `memex:SoftwareSystem2`|
