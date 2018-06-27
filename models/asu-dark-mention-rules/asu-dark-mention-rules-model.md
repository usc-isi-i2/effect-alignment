# dark-mention-rules-cdr.jl

## Add Column

## Add Node/Literal
#### Literal Node: `JSON`
Literal Type: ``
<br/>Language: ``
<br/>isUri: `false`


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

#### _forumIds_clean_
From column: _json_rep / forumIds_
``` python
x = getValue("forumIds").strip()
len_x = len(x)
if len_x > 2:
  return x[1:len_x-1]
x = getValue("restrictForums")
if len(x) > 0 and x.lower() == "true":
   return "NONE"
```

#### _marketIds_clean_
From column: _json_rep / marketIds_
``` python
x = getValue("marketIds").strip()
len_x = len(x)
if len_x > 2:
  return x[1:len_x-1]
x = getValue("restrictMarketplaces")
if len(x) > 0 and x.lower() == "true":
   return "NONE"
```

#### _attack_uri_
From column: _json_rep / targetSystem_uri_
``` python
return "attack/" + SM.md5_hash(getValue("raw_content"))
```

#### _code_uri_
From column: _raw_content_
``` python
return "attack/" + SM.md5_hash(getValue("raw_content")) + "/code"
```

#### _forum_uri_
From column: _json_rep / forumIds_clean_split / Values_
``` python
x = getValue("Values").strip()
if len(x) > 0:
   return "forum/" + x
```

#### _marketplace_uri_
From column: _json_rep / marketIds_clean_split / Values_
``` python
x = getValue("Values").strip()
if len(x) > 0:
  return "marketplace/" + x
```

#### _numAttacks_clean_
From column: _json_rep / numberOfAttacks_
``` python
x = getValue("numberOfAttacks")
if len(x) > 0:
   return SM.numeric_only(x)
return "0"
```


## Selections

## Semantic Types
| Column | Property | Class |
|  ----- | -------- | ----- |
| __id_ | `schema:source`<BR> - _specified provenance_ | `memex:PersonOrOrganization1`|
| _attack_uri_ | `uri` | `memex:AttackEvent1`|
| _code_uri_ | `uri` | `schema:Code1`|
| _cpe_cluster_uri_ | `uri` | `memex:SoftwareSystemCluster1`|
| _dateRuleUpdated_iso_ | `schema:dateCreated` | `memex:AttackEvent1`|
| _eventType_ | `memex:hasType` | `memex:AttackEvent1`|
| _forum_uri_ | `uri` | `memex:Forum1`|
| _marketplace_uri_ | `uri` | `memex:PersonOrOrganization2`|
| _numAttacks_clean_ | `memex:numberOfAttacks` | `memex:AttackEvent1`|
| _probability_ | `memex:probabilityOfOccurance` | `memex:AttackEvent1`|
| _raw_content_ | `schema:text` | `schema:Code1`|
| _ruleType_ | `schema:category` | `memex:AttackEvent1`|
| _source_name_ | `schema:publisher` | `memex:AttackEvent1`|
| _targetSystem_ | `schema:name` | `memex:PersonOrOrganization1`|
| _targetSystem_uri_ | `uri` | `memex:PersonOrOrganization1`|
| _timeLagDays_iso_ | `schema:duration` | `memex:AttackEvent1`|
| _timestamp_iso_ | `memex:dateRecorded`<BR> - _specified provenance_ | `memex:PersonOrOrganization1`|


## Links
| From | Property | To |
|  --- | -------- | ---|
| `memex:AttackEvent1` | `memex:attackOnSoftwareCluster` | `memex:SoftwareSystemCluster1`|
| `memex:AttackEvent1` | `memex:affected` | `memex:PersonOrOrganization1`|
| `memex:AttackEvent1` | `schema:seller` | `memex:PersonOrOrganization2`|
| `memex:AttackEvent1` | `schema:recordedIn` | `schema:Code1`|
| `memex:AttackEvent1` | `memex:isMentionedIn` | `memex:Forum1`|
| `schema:Code1` | `schema:inLanguage` | `JSON`|
