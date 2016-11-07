## linkedSource-for-karma.jl

### PyTransforms
#### _username_sha1_
From column: _json_rep / data / username_
>``` python
return SM.sha1_hash(getValue("username"))
```

#### _password_sha1_
From column: _json_rep / data / Real_Password_
>``` python
return SM.sha1_hash(getValue("Real_Password"))
```

#### _email_domain_
From column: _json_rep / data / email_
>``` python
return getValue("email").split("@")[1]
```

#### _email_name_sha1_
From column: _json_rep / data / email_
>``` python
return SM.sha1_hash(getValue("email").split("@")[0])
```

#### _cdr_id_
From column: __id_
>``` python
return "identifier/"+getValue("_id")
```


### Semantic Types
| Column | Property | Class |
|  ----- | -------- | ----- |
| _cdr_id_ | `schema:source` | `memex:Exploit1`|
| _database_ | `schema:name` | `memex:PersonOrOrganization1`|
| _email_domain_ | `rdfs:domain` | `memex:EmailAddress1`|
| _email_name_sha1_ | `memex:nameSHA1` | `memex:EmailAddress1`|
| _password_sha1_ | `memex:nameSHA1` | `memex:Password1`|
| _source_name_ | `schema:publisher` | `memex:Exploit1`|
| _username_sha1_ | `memex:nameSHA1` | `memex:UserName1`|


### Links
| From | Property | To |
|  --- | -------- | ---|
| `memex:Exploit1` | `memex:itemStolen` | `memex:LoginCredentials1`|
| `memex:LoginCredentials1` | `memex:emailAddress` | `memex:EmailAddress1`|
| `memex:LoginCredentials1` | `memex:organization` | `memex:PersonOrOrganization1`|
| `memex:LoginCredentials1` | `memex:password` | `memex:Password1`|
| `memex:LoginCredentials1` | `memex:username` | `memex:UserName1`|
