# news_data-cdr.jl

## Add Column

## Add Node/Literal

## PyTransforms
#### _datePublished_iso_
From column: _json_rep / date_published_
``` python
return DM.iso8601date(getValue("date_published"), "%Y-%m-%dT%H:%M:%S+00:00")
```

#### _cve_uri_
From column: _json_rep / extractions / cve / result / value_
``` python
x = getValue("value")
if len(x) > 0:
  return "vulnerability/" + x.upper()
return ''
```

#### _ms_uri_
From column: _json_rep / extractions / msid / result / value_
``` python
x = getValue("value").strip()
if len(x) > 0:
   return "securityUpdate/" + x.upper()
```

#### _news_uri_
From column: _json_rep / url_
``` python
url = getValue("url")
if len(url) > 0:
   return UM.uri_from_fields("news/", url)
```

#### _extraction_uri_
From column: _json_rep / extractions / json_rep.text / text_
``` python
x = getValue("text").strip()
uri = getValue("news_uri")
if len(x) > 0:
  x = re.sub('[^A-Za-z0-9]+', '', x)
  return uri + "/extraction/" + getValue("label") + "/" + x
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
| __id_ | `schema:source`<BR> - _specified provenance_ | `memex:Extraction1`|
| _author_ | `schema:author` | `schema:NewsArticle1`|
| _category_ | `schema:category` | `schema:NewsArticle1`|
| _cve_uri_ | `uri` | `memex:Vulnerability1`|
| _datePublished_iso_ | `schema:datePublished` | `schema:NewsArticle1`|
| _extraction_uri_ | `uri` | `memex:Extraction1`|
| _extractor_ | `memex:extractor` | `memex:Extraction1`|
| _label_ | `memex:hasType` | `memex:Extraction1`|
| _ms_uri_ | `uri` | `memex:SecurityUpdate1`|
| _news_uri_ | `uri` | `schema:NewsArticle1`|
| _readable_text_ | `schema:text` | `schema:NewsArticle1`|
| _source_ | `schema:producer` | `schema:NewsArticle1`|
| _source_name_ | `schema:publisher`<BR> - _specified provenance_ | `memex:Extraction1`|
| _text_ | `schema:text` | `memex:Extraction1`|
| _timestamp_iso_ | `memex:dateRecorded`<BR> - _specified provenance_ | `memex:Extraction1`|
| _title_ | `schema:title` | `schema:NewsArticle1`|
| _url_ | `schema:url` | `schema:NewsArticle1`|


## Links
| From | Property | To |
|  --- | -------- | ---|
| `schema:NewsArticle1` | `schema:mentions` | `memex:Vulnerability1`|
| `schema:NewsArticle1` | `memex:hasExtraction` | `memex:Extraction1`|
| `schema:NewsArticle1` | `memex:mentionsSecurityUpdate` | `memex:SecurityUpdate1`|
