# ransomware.csv

## Add Column

## Add Node/Literal

## PyTransforms
#### _URLHash_
From column: _URL_
``` python
return  "malware/" + SM.md5_hash(getValue("URL"))
```

#### _observed_iso_
From column: _Firstseen (UTC)_
``` python
return DM.iso8601date(getValue("Firstseen (UTC)"))
```


## Selections

## Semantic Types
| Column | Property | Class |
|  ----- | -------- | ----- |
| _Country_ | `schema:countryOfOrigin` | `memex:Malware1`|
| _Malware_ | `schema:name` | `memex:Malware1`|
| _Registrar_ | `memex:registrar` | `memex:IPAddress1`|
| _URL_ | `schema:url` | `memex:Malware1`|
| _URLHash_ | `uri` | `memex:Malware1`|
| _Values_ | `schema:name` | `memex:IPAddress1`|
| _Values_ | `memex:autonomousSystemNumber` | `memex:IPAddress1`|
| _observed_iso_ | `memex:observedDate` | `memex:Malware1`|


## Links
| From | Property | To |
|  --- | -------- | ---|
| `memex:Malware1` | `memex:hostedAt` | `memex:IPAddress1`|
