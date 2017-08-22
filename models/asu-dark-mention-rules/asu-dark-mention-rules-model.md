# dark-mention-rules-cdr.jl

## Add Column

## Add Node/Literal

## PyTransforms
#### _cpe_cluster_uri_
From column: _json_rep / cpeGroup_
``` python
x = getValue("cpeGroup").strip()
if len(x) > 0:
  x = re.sub('[^A-Za-z0-9\|]+', '', x.strip())
  x= x.replace("|", "_")
  return "cpeCluster/" + x
```

#### _dateRuleUpdated_iso_
From column: _json_rep / dateRuleUpdated_
``` python
return DM.iso8601date(getValue("dateRuleUpdated"), "%Y-%m-%d %H:%M:%S.%f")
```

#### _rule_end_date_
From column: _json_rep / timeLagDays_
``` python
x = getValue("dateRuleUpdated_iso")
startDate = datetime.strptime(x, "%Y-%m-%dT%H:%M:%S")
lag = getValue("timeLagDays")
delta = timedelta(days=int(lag))
endDate = startDate + delta
return endDate.isoformat()
return default_time
```

#### _targetSystem_uri_
From column: _json_rep / targetSystem_
``` python
x = getValue("targetSystem")
if len(x) > 0:
   return UM.uri_from_fields("organization/", x)
```

#### _timeLagDays_iso_
From column: _json_rep / timeLagDays_
``` python
x = getValue("timeLagDays")
if len(x) > 0:
   return "P" + x + "D"
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
| __id_ | `schema:source`<BR> - _specified provenance_ | `memex:AttackEvent1`|
| _cpe_cluster_uri_ | `uri` | `memex:SoftwareSystemCluster1`|
| _dateRuleUpdated_iso_ | `schema:startDate` | `memex:AttackEvent1`|
| _eventType_ | `memex:hasType` | `memex:AttackEvent1`|
| _probability_ | `memex:probabilityOfOccurance` | `memex:AttackEvent1`|
| _rule_end_date_ | `schema:endDate` | `memex:AttackEvent1`|
| _source_name_ | `schema:publisher` | `memex:AttackEvent1`|
| _targetSystem_ | `schema:name` | `memex:PersonOrOrganization1`|
| _targetSystem_uri_ | `uri` | `memex:PersonOrOrganization1`|
| _timeLagDays_iso_ | `schema:duration` | `memex:AttackEvent1`|
| _timestamp_iso_ | `memex:dateRecorded`<BR> - _specified provenance_ | `memex:AttackEvent1`|


## Links
| From | Property | To |
|  --- | -------- | ---|
| `memex:AttackEvent1` | `memex:affected` | `memex:PersonOrOrganization1`|
| `memex:AttackEvent1` | `memex:attackOnSoftwareCluster` | `memex:SoftwareSystemCluster1`|
