## hackingposts-for-karma.jl

### PyTransforms
#### _topic_id_
From column: _json_rep / topicId_
``` python
return "topicid/"+getValue("topicId")
```

#### _post_id_
From column: _json_rep / postsId_
``` python
return getValue("topic_id_new")+"/"+"postid/"+getValue("postsId")
```

#### _forums_id_
From column: _json_rep / forumsId_
``` python
return "forumsid/"+getValue("forumsId")
```

#### _posted_date_iso_
From column: _json_rep / postedDate_
``` python
t = getValue("postedDate")
return DM.iso8601date(t,"%Y-%m-%d")
```

#### _users_id_
From column: _json_rep / usersId_
``` python
return "usersid/"+getValue("forumsId") + "/"+ getValue("usersId")
```

#### _topic_id_new_
From column: _json_rep / topic_id_
``` python
return getValue("forums_id")+"/"+"topicid/"+getValue("topicId")
```

#### _login_credentials_uri_
From column: _json_rep / users_id_
``` python
return "identifier/"+"forumsid/"+getValue("forumsId")+"/"+"usersid/"+getValue("usersId")
```

#### _person_id_
From column: _json_rep / usersId_
``` python
return "person/" + getValue("forumsId") + "/" + getValue("usersId")
```


### Semantic Types
| Column | Property | Class |
|  ----- | -------- | ----- |
| _forums_id_ | `uri` | `memex:Forum1`|
| _language_ | `schema:language` | `memex:Post1`|
| _login_credentials_uri_ | `uri` | `memex:LoginCredentials1`|
| _person_id_ | `uri` | `memex:PersonOrOrganization1`|
| _postContent_ | `schema:text` | `memex:Post1`|
| _post_id_ | `uri` | `memex:Post1`|
| _posted_date_iso_ | `schema:datePublished` | `memex:Post1`|
| _topic_id_new_ | `uri` | `memex:Topic1`|
| _topicsName_ | `schema:name` | `memex:Topic1`|
| _users_id_ | `uri` | `memex:UserName1`|


### Links
| From | Property | To |
|  --- | -------- | ---|
| `memex:Forum1` | `memex:hasTopic` | `memex:Topic1`|
| `memex:LoginCredentials1` | `memex:username` | `memex:UserName1`|
| `memex:PersonOrOrganization1` | `memex:hasLoginCredentials` | `memex:LoginCredentials1`|
| `memex:PersonOrOrganization1` | `memex:isAuthorOf` | `memex:Post1`|
| `memex:Post1` | `memex:isPostOf` | `memex:Topic1`|
| `memex:Post1` | `schema:author` | `memex:PersonOrOrganization1`|
| `memex:Topic1` | `memex:isTopicOf` | `memex:Forum1`|
| `memex:Topic1` | `memex:hasPost` | `memex:Post1`|
