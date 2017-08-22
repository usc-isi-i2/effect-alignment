# dark-mentions-cdr.jl

## Add Column

## Add Node/Literal

## PyTransforms
#### _cve_uri_
From column: _json_rep / CVE_
``` python
x = getValue("CVE").strip()
if len(x) > 0:
   return "vulnerability/"+x.upper()
```

#### _cpe_cluster_uri_
From column: _json_rep / clusterTags / values_
``` python
x = getValue("values").strip()
if len(x) > 0:
  x = re.sub('[^A-Za-z0-9\|]+', '', x.strip())
  x= x.replace("|", "_")
  return "cpeCluster/" + x
```

#### _timestamp_iso_
From column: _timestamp_
``` python
return DM.iso8601date(getValue("timestamp"))
```


## Selections

## Semantic Types
| Column | Property | Class |
|  ----- | -------- | ----- |
| __id_ | `schema:source`<BR> - _specified provenance_ | `memex:SoftwareSystemCluster1`|
| _cpe_cluster_uri_ | `uri` | `memex:SoftwareSystemCluster1`|
| _cve_uri_ | `uri` | `memex:Vulnerability1`|
| _source_name_ | `schema:publisher`<BR> - _specified provenance_ | `memex:SoftwareSystemCluster1`|
| _timestamp_iso_ | `memex:dateRecorded`<BR> - _specified provenance_ | `memex:SoftwareSystemCluster1`|
| _values_ | `schema:name` | `memex:SoftwareSystemCluster1`|


## Links
| From | Property | To |
|  --- | -------- | ---|
| `memex:Vulnerability1` | `memex:vulnerabilityOfCluster` | `memex:SoftwareSystemCluster1`|
