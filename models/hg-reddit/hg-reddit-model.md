# reddit-cdr-extractions.jl

## Add Column

## Add Node/Literal

## PyTransforms
#### _author_uri_
From column: _json_rep / author_
``` python
x = getValue("author")
if len(x) > 0:
  return "forum/reddit/user/" + x
```

#### _reddit_url_
From column: _json_rep / permalink_
``` python
return "http://www.reddit.com" + getValue("permalink")
```

#### _reddit_uri_
From column: _json_rep / reddit_url_
``` python
return "forum/reddit/post" + getValue("permalink")
```

#### _created_iso_
From column: _json_rep / created_utc_
``` python
utc = str(int(float(getValue("created_utc"))))
return DM.iso8601date(utc)
```

#### _selftext_with_links_
From column: _json_rep / selftext_
``` python
links = json.loads(getValue("links"))
all_links = []
for x in links:
  all_links.append(x['values'])
return getValue("title") + "\n\n" + getValue("selftext") + " Links: " + ", ".join(all_links)
```

#### _comment_created_iso_
From column: _json_rep / comments / created_utc_
``` python
return DM.iso8601date(str(int(float(getValue("created_utc")))))
```

#### _comment_uri_
From column: _json_rep / comments / id_
``` python
return getValue("reddit_uri") + "comment/" + getValue("id")
```

#### _comment_author_
From column: _json_rep / comments / author_
``` python
x = getValue("author")
if len(x) > 0:
  return "forum/reddit/user/" + x
```

#### _cve_uri_
From column: _extractions / cve / result / value_
``` python
x= getValue("value")
if len(x) > 0:
  return "vulnerability/"+getValue("value").upper()
return ''
```

#### _msid_uri_
From column: _extractions / msid / result / value_
``` python
x = getValue("value").strip()
if len(x) > 0:
   return "securityUpdate/" + x.upper()
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
| __id_ | `schema:source`<BR> - _specified provenance_ | `schema:Comment1`|
| _author_uri_ | `uri` | `memex:PersonOrOrganization1`|
| _body_ | `schema:text` | `schema:Comment1`|
| _comment_author_ | `uri` | `memex:PersonOrOrganization2`|
| _comment_created_iso_ | `schema:datePublished` | `schema:Comment1`|
| _comment_uri_ | `uri` | `schema:Comment1`|
| _created_iso_ | `schema:datePublished` | `memex:Post1`|
| _cve_uri_ | `uri` | `memex:Vulnerability1`|
| _msid_uri_ | `uri` | `memex:SecurityUpdate1`|
| _reddit_uri_ | `uri` | `memex:Post1`|
| _reddit_url_ | `schema:url` | `memex:Post1`|
| _selftext_with_links_ | `schema:text` | `memex:Post1`|
| _source_name_ | `schema:publisher`<BR> - _specified provenance_ | `schema:Comment1`|
| _timestamp_iso_ | `memex:dateRecorded`<BR> - _specified provenance_ | `memex:Post1`|


## Links
| From | Property | To |
|  --- | -------- | ---|
| `memex:Post1` | `schema:author` | `memex:PersonOrOrganization1`|
| `memex:Post1` | `memex:mentionsSecurityUpdate` | `memex:SecurityUpdate1`|
| `memex:Post1` | `schema:mentions` | `memex:Vulnerability1`|
| `memex:Post1` | `schema:comment` | `schema:Comment1`|
| `schema:Comment1` | `schema:author` | `memex:PersonOrOrganization2`|
