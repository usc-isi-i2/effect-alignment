# news-cdr.jl

## Add Column

## Add Node/Literal

## PyTransforms
#### _value_
From column: _json_rep / extractions / msid / result / value_
``` python
x = getValue("value").strip()
if len(x) > 0:
   return "securityUpdate/" + x.upper()
```

#### _date_published_iso_
From column: _json_rep / date_published_
``` python
return DM.iso8601date(getValue("timestamp"))
```

#### _news_uri_
From column: _json_rep / url_
``` python
return UM.uri_from_fields("news/", getValue("url"))
```


## Selections

## Semantic Types
| Column | Property | Class |
|  ----- | -------- | ----- |
| _author_ | `schema:author` | `schema:NewsArticle1`|
| _category_ | `schema:category` | `schema:NewsArticle1`|
| _date_published_ | `schema:datePublished`<BR> - _specified provenance_ | `schema:NewsArticle1`|
| _news_uri_ | `uri` | `schema:NewsArticle1`|
| _readable_text_ | `schema:text` | `schema:NewsArticle1`|
| _readable_title_ | `schema:title` | `schema:NewsArticle1`|
| _source_ | `memex:hostedAt` | `schema:NewsArticle1`|
| _source_name_ | `schema:publisher`<BR> - _specified provenance_ | `schema:NewsArticle1`|
| _url_ | `schema:url` | `schema:NewsArticle1`|
| _value_ | `uri` | `memex:Vulnerability1`|
| _value_ | `uri` | `memex:SecurityUpdate1`|


## Links
| From | Property | To |
|  --- | -------- | ---|
| `schema:NewsArticle1` | `memex:mentionsSecurityUpdate` | `memex:SecurityUpdate1`|
| `schema:NewsArticle1` | `schema:mentions` | `memex:Vulnerability1`|
