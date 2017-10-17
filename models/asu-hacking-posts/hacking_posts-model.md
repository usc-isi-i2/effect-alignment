# hackingpostsCDR-extractions.jl

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

#### _extraction_uri_
From column: _extractions / json_rep.postContent / text_
``` python
x = getValue("text").strip()
if len(x) >0:
    x = re.sub('[^A-Za-z0-9]+', '', x)
    post_uri = "post/" + SM.md5_hash(getValueFromNestedColumnByIndex("json_rep", "post_id", getRowIndex()))
    label_value = getValue("label")
    return post_uri+'/extraction/'+label_value+'/'+x

```

#### _post_date_iso_
From column: _json_rep / postedDate_
``` python
t = getValue("postedDate")
return DM.iso8601date(t,"%Y-%m-%d")
```

#### _user_id_
From column: _json_rep / uid_
``` python
return getValue("forum_id") + "/user/" + getValue("uid")
```

#### _person_id_
From column: _json_rep / user_id_
``` python
return "logincredentials/" + getValue("forum_id") + "/user/" + getValue("uid")
```

#### _cdr_id_
From column: __id_
``` python
return getValue("_id")
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
| _cdr_id_ | `schema:source`<BR> - _specified provenance_ | `memex:Post1`|
| _cve_uri_ | `uri` | `memex:Vulnerability1`|
| _dateRecorded_ | `memex:dateRecorded`<BR> - _specified provenance_ | `memex:Topic1`|
| _extraction_uri_ | `uri` | `memex:Extraction1`|
| _extractor_ | `memex:extractor` | `memex:Extraction1`|
| _forum_id_ | `uri` | `memex:Forum1`|
| _label_ | `memex:hasType` | `memex:Extraction1`|
| _language_ | `schema:language` | `memex:Post1`|
| _msid_uri_ | `uri` | `memex:SecurityUpdate1`|
| _originalContent_ | `schema:translationOfWork` | `memex:Post1`|
| _person_id_ | `uri` | `memex:LoginCredentials1`|
| _postContent_ | `schema:text` | `memex:Post1`|
| _post_id_ | `uri` | `memex:Post1`|
| _recordedDateTimeISO_ | `schema:datePublished` | `memex:Post1`|
| _source_name_ | `schema:publisher`<BR> - _specified provenance_ | `memex:Post1`|
| _text_ | `schema:text` | `memex:Extraction1`|
| _topic_id_ | `uri` | `memex:Topic1`|
| _topicsName_ | `schema:name` | `memex:Topic1`|
| _user_id_ | `uri` | `memex:PersonOrOrganization1`|
| _values_ | `memex:financialTags` | `memex:Post1`|
| _values_ | `memex:softwareTags` | `memex:Post1`|
| _values_ | `schema:keywords` | `memex:Post1`|


## Links
| From | Property | To |
|  --- | -------- | ---|
| `memex:Forum1` | `memex:hasTopic` | `memex:Topic1`|
| `memex:PersonOrOrganization1` | `memex:hasLoginCredentials` | `memex:LoginCredentials1`|
| `memex:Post1` | `memex:mentionsSecurityUpdate` | `memex:SecurityUpdate1`|
| `memex:Post1` | `memex:hasTopic` | `memex:Topic1`|
| `memex:Post1` | `schema:author` | `memex:PersonOrOrganization1`|
| `memex:Post1` | `schema:mentions` | `memex:Vulnerability1`|
| `memex:Post1` | `memex:hasExtraction` | `memex:Extraction1`|
| `memex:Topic1` | `memex:isTopicOf` | `memex:Forum1`|
| `memex:Topic1` | `memex:hasPost` | `memex:Post1`|
| `memex:Vulnerability1` | `memex:isMentionedIn` | `memex:Post1`|
