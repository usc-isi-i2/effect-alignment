## nvdcve-2.0-2003.xml

### PyTransforms
#### _vulnerability_uri_
From column: _nvd / entry / id_
>``` python
return 'vulnerability/' + getValue("id").lower()
```

#### _identifier_vulnerability_uri_
From column: _nvd / entry / id_
>``` python
return 'identifier/cve/' + getValue("id").lower()
```

#### _access_complexity_
From column: _nvd / entry / vuln:cvss / cvss:base_metrics / cvss:access-complexity_
>``` python
record_value = getValue("cvss:access-complexity")
record_value = json.loads(record_value)[0]

value = record_value['values']
if value.strip() == '':
    value = record_value['content']

return value




```

#### _access_vector_
From column: _nvd / entry / vuln:cvss / cvss:base_metrics / cvss:access-vector_
>``` python
record_value = getValue("cvss:access-vector")
record_value = json.loads(record_value)[0]

value = record_value['values']
if value.strip() == '':
    value = record_value['content']

return value




```

#### _authentication_
From column: _nvd / entry / vuln:cvss / cvss:base_metrics / cvss:authentication_
>``` python
record_value = getValue("cvss:authentication")
record_value = json.loads(record_value)[0]

value = record_value['values']
if value.strip() == '':
    value = record_value['content']

return value
```

#### _availability-impact_
From column: _nvd / entry / vuln:cvss / cvss:base_metrics / cvss:availability-impact_
>``` python
record_value = getValue("cvss:availability-impact")
record_value = json.loads(record_value)[0]

value = record_value['values']
if value.strip() == '':
    value = record_value['content']

return value

```

#### _confidentiality-impact_
From column: _nvd / entry / vuln:cvss / cvss:base_metrics / cvss:confidentiality-impact_
>``` python
record_value = getValue("cvss:confidentiality-impact")
record_value = json.loads(record_value)[0]

value = record_value['values']
if value.strip() == '':
    value = record_value['content']

return value

```

#### _generated_on_datetime_
From column: _nvd / entry / vuln:cvss / cvss:base_metrics / cvss:generated-on-datetime_
>``` python
dt = getValue("cvss:generated-on-datetime")
dt = dt[:-5] + dt[-5:].replace(':', '')
dt = DM.iso8601date(dt, '%Y-%m-%dT%H:%M:%S.%f%Z')
return dt
```

#### _integrity-impact_
From column: _nvd / entry / vuln:cvss / cvss:base_metrics / cvss:integrity-impact_
>``` python
record_value = getValue("cvss:integrity-impact")
record_value = json.loads(record_value)[0]

value = record_value['values']
if value.strip() == '':
    value = record_value['content']

return value

```

#### _vuln-last-modified-dt_
From column: _nvd / entry / vuln:last-modified-datetime_
>``` python
dt = getValue("vuln:last-modified-datetime")
dt = dt[:-5] + dt[-5:].replace(':', '')
dt = DM.iso8601date(dt, '%Y-%m-%dT%H:%M:%S.%f%Z')
return dt
```

#### _vuln-published-dt_
From column: _nvd / entry / vuln:published-datetime_
>``` python
dt = getValue("vuln:published-datetime")
dt = dt[:-5] + dt[-5:].replace(':', '')
dt = DM.iso8601date(dt, '%Y-%m-%dT%H:%M:%S.%f%Z')
return dt
```

#### _software_system_uri_
From column: _nvd / entry / vuln:vulnerable-software-list / vuln:product / values_
>``` python
return "software-system-release/" + getValue("values").replace("/", '-').replace(':', '@').lower()
```

#### _software_version_
From column: _nvd / entry / vuln:vulnerable-software-list / vuln:product / values_
>``` python
cpe = getValue("values")
return cpe.split(':')[4]
```

#### _software_name_
From column: _nvd / entry / vuln:vulnerable-software-list / vuln:product / values_
>``` python
cpe = getValue("values")
return cpe.split(':')[3]
```


### Semantic Types
| Column | Property | Class |
|  ----- | -------- | ----- |
| _access_complexity_ | `memex:cvssComplexity` | `memex:CVSS1`|
| _access_vector_ | `memex:cvssAccessVector` | `memex:CVSS1`|
| _authentication_ | `memex:cvssAuthentication` | `memex:CVSS1`|
| _availability-impact_ | `memex:cvssAvailability` | `memex:CVSS1`|
| _confidentiality-impact_ | `memex:cvssConfidentiality` | `memex:CVSS1`|
| _cvss:score_ | `memex:cvssScore` | `memex:CVSS1`|
| _cvss:source_ | `schema:source` | `memex:CVSS1`|
| _generated_on_datetime_ | `schema:datePublished` | `memex:CVSS1`|
| _href_ | `schema:source` | `memex:Vulnerability1`|
| _id_ | `rdfs:label` | `memex:Identifier1`|
| _identifier_vulnerability_uri_ | `uri` | `memex:Identifier1`|
| _integrity-impact_ | `memex:cvssIntegrity` | `memex:CVSS1`|
| _software_name_ | `schema:name` | `memex:SoftwareSystem1`|
| _software_system_uri_ | `uri` | `memex:SoftwareSystem1`|
| _software_version_ | `schema:version` | `memex:SoftwareSystem1`|
| _values_ | `rdfs:label` | `memex:Identifier2`|
| _vuln-last-modified-dt_ | `schema:dateModified` | `memex:Vulnerability1`|
| _vuln-published-dt_ | `schema:datePublished` | `memex:Vulnerability1`|
| _vuln:summary_ | `schema:description` | `memex:Vulnerability1`|
| _vulnerability_uri_ | `uri` | `memex:Vulnerability1`|


### Links
| From | Property | To |
|  --- | -------- | ---|
| `memex:Identifier1` | `memex:hasType` | `xsd:cve`|
| `memex:Identifier2` | `memex:hasType` | `xsd:cpe`|
| `memex:SoftwareSystem1` | `memex:identifier` | `memex:Identifier2`|
| `memex:Vulnerability1` | `memex:hasCVSS` | `memex:CVSS1`|
| `memex:Vulnerability1` | `memex:identifier` | `memex:Identifier1`|
| `memex:Vulnerability1` | `memex:vulnerabilityOf` | `memex:SoftwareSystem1`|
