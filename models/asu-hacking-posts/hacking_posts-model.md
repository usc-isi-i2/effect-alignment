# hackingposts-for-karma.jl

## Add Column

## Add Node/Literal

## PyTransforms
#### _forum_id_
From column: _json_rep / forumsId_
``` python
return "forum/" + getValue("forumsId")
```

#### _topic_id_
From column: _json_rep / topicId_
``` python
return getValue("forum_id") + "/topic/" + SM.sha1_hash(getValue("topicsName"))
```

#### _post_id_
From column: _json_rep / postsId_
``` python
return getValue("topic_id") + "/post/" + SM.sha1_hash(getValue("postContent"))
```

#### _post_date_iso_
From column: _json_rep / postedDate_
``` python
t = getValue("postedDate")
return DM.iso8601date(t,"%Y-%m-%d")
```

#### _user_id_
From column: _json_rep / usersId_
``` python
return getValue("forum_id") + "/user/" + getValue("usersId")
```

#### _person_id_
From column: _json_rep / user_id_
``` python
return "logincredentials/" + getValue("forum_id") + "/user/" + getValue("usersId")
```

#### _cdr_id_
From column: __id_
``` python
return getValue("_id")
```

#### _cve_id_
From column: _json_rep / cve / Values_
``` python
cve = getValue("Values")
if cve:
  return "vulnerability/" + cve.upper() 
return ''
```

#### _dateRecorded_
From column: _timestamp_
``` python
return DM.iso8601date(getValue("timestamp"), "%Y-%m-%d %H:%M:%S.%f")
```


## Selections

## Semantic Types
| Column | Property | Class |
|  ----- | -------- | ----- |
| _cdr_id_ | `schema:source`<BR> - _specified provenance_ | `memex:Forum1`|
| _cve_id_ | `uri` | `memex:Vulnerability1`|
| _dateRecorded_ | `memex:dateRecorded`<BR> - _specified provenance_ | `memex:Forum1`|
| _forum_id_ | `uri` | `memex:Forum1`|
| _language_ | `schema:language` | `memex:Post1`|
| _person_id_ | `uri` | `memex:LoginCredentials1`|
| _postContent_ | `schema:text` | `memex:Post1`|
| _post_date_iso_ | `schema:datePublished` | `memex:Post1`|
| _post_id_ | `uri` | `memex:Post1`|
| _source_name_ | `schema:publisher`<BR> - _specified provenance_ | `memex:Forum1`|
| _topic_id_ | `uri` | `memex:Topic1`|
| _topicsName_ | `schema:name` | `memex:Topic1`|
| _user_id_ | `uri` | `memex:PersonOrOrganization1`|


## Links
| From | Property | To |
|  --- | -------- | ---|
| `memex:Forum1` | `memex:hasTopic` | `memex:Topic1`|
| `memex:PersonOrOrganization1` | `memex:hasLoginCredentials` | `memex:LoginCredentials1`|
| `memex:Post1` | `memex:hasTopic` | `memex:Topic1`|
| `memex:Post1` | `schema:author` | `memex:PersonOrOrganization1`|
| `memex:Post1` | `schema:mentions` | `memex:Vulnerability1`|
| `memex:Topic1` | `memex:hasPost` | `memex:Post1`|
| `memex:Topic1` | `memex:isTopicOf` | `memex:Forum1`|
| `memex:Vulnerability1` | `memex:isMentionedIn` | `memex:Post1`|
