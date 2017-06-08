# twitterCDR-extractions.jl

## Add Column

## Add Node/Literal

## PyTransforms
#### _tweet_uri_
From column: _json_rep / tweet_id_
``` python
id = getValue("tweet_id")
if len(id) > 0:
   return "tweet/" + id
```

#### _username_clean_
From column: _json_rep / userName_
``` python
x = getValue("userName")
if len(x) > 0:
  if x.startswith("@"):
    x = x[1:]
    return x
```

#### _user_login_uri_
From column: _json_rep / username_clean_
``` python
x = getValue("username_clean")
if len(x) > 0:
   return "logincredentials/twitter/" + x
```

#### _person_uri_
From column: _json_rep / user_login_uri_
``` python
x = getValue("username_clean")
if len(x) > 0:
   return "personOrOrganization/twitter/" + x
```

#### _tags_clean_
From column: _json_rep / hastags_split / Values_
``` python
x = getValue("Values").strip()
len_x = len(x)
if len_x > 0:
   if x.startswith("u'"):
        return x[2:len_x-1]
   return x
```

#### _mentions_clean_
From column: _json_rep / mentios_values / Values_
``` python
x = getValue("Values").strip()
len_x = len(x)
if len_x > 0:
   if x.startswith("u'"):
        return x[2:len_x-1]
   return x
```

#### _mentions_uri_
From column: _json_rep / mentios_values / mentions_clean_
``` python
x = getValue("mentions_clean").strip()
len_x = len(x)
if (len) > 0:
   return "personOrOrganization/" + x
```

#### _recorded_time_iso_
From column: _json_rep / recorded_time_seconds_
``` python
return DM.iso8601date(getValue("recorded_time_seconds"), "%a %b %d %H:%M:%S UTC %Y")
```

#### _timestamp_iso_
From column: _timestamp_
``` python
return DM.iso8601date(getValue("timestamp"))
```

#### _username_uri_
From column: _json_rep / user_login_uri_
``` python
x = getValue("username_clean")
if len(x) > 0:
   return "username/twitter/" + x
```

#### _tweet_uri2_
From column: _extractions / json_rep.tweetContent_
``` python
return getValueFromNestedColumnByIndex("json_rep", "tweet_uri", getRowIndex())
```

#### _extraction_uri_
From column: _extractions / json_rep.tweetContent / text_
``` python
tweet_uri = getValue("tweet_uri2")
x = getValue("text").strip()
if len(x) > 0:
   x = re.sub('[^A-Za-z0-9]+', '', x)
   return tweet_uri + "/extraction/" + getValue("label") + "/" + x
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


## Selections

## Semantic Types
| Column | Property | Class |
|  ----- | -------- | ----- |
| __id_ | `schema:source`<BR> - _specified provenance_ | `schema:SocialMediaPosting1`|
| _content_type_ | `memex:hasType` | `schema:SocialMediaPosting1`|
| _cve_uri_ | `uri` | `memex:Vulnerability1`|
| _extraction_uri_ | `uri` | `memex:Extraction1`|
| _extractor_ | `memex:extractor` | `memex:Extraction1`|
| _favorites_ | `memex:favoriteCount` | `schema:SocialMediaPosting1`|
| _label_ | `memex:hasType` | `memex:Extraction1`|
| _mentions_uri_ | `uri` | `memex:PersonOrOrganization2`|
| _msid_uri_ | `uri` | `memex:SecurityUpdate1`|
| _person_uri_ | `uri` | `memex:PersonOrOrganization1`|
| _recorded_time_iso_ | `schema:datePublished` | `schema:SocialMediaPosting1`|
| _retweet_ | `memex:repostCount` | `schema:SocialMediaPosting1`|
| _source_name_ | `schema:publisher`<BR> - _specified provenance_ | `schema:SocialMediaPosting1`|
| _tags_clean_ | `schema:keywords` | `schema:SocialMediaPosting1`|
| _text_ | `schema:text` | `memex:Extraction1`|
| _timestamp_iso_ | `memex:dateRecorded`<BR> - _specified provenance_ | `schema:SocialMediaPosting1`|
| _tweetContent_ | `schema:text` | `schema:SocialMediaPosting1`|
| _tweet_uri_ | `uri` | `schema:SocialMediaPosting1`|
| _user_login_uri_ | `uri` | `memex:LoginCredentials1`|
| _username_clean_ | `schema:name` | `memex:UserName1`|
| _username_uri_ | `uri` | `memex:UserName1`|


## Links
| From | Property | To |
|  --- | -------- | ---|
| `memex:LoginCredentials1` | `memex:username` | `memex:UserName1`|
| `memex:PersonOrOrganization1` | `memex:hasLoginCredentials` | `memex:LoginCredentials1`|
| `schema:SocialMediaPosting1` | `memex:hasExtraction` | `memex:Extraction1`|
| `schema:SocialMediaPosting1` | `memex:mentionsPersonOrOrganization` | `memex:PersonOrOrganization2`|
| `schema:SocialMediaPosting1` | `memex:mentionsSecurityUpdate` | `memex:SecurityUpdate1`|
| `schema:SocialMediaPosting1` | `schema:author` | `memex:PersonOrOrganization1`|
| `schema:SocialMediaPosting1` | `schema:mentions` | `memex:Vulnerability1`|
