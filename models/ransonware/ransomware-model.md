# ransomware.csv

## Add Column

## Add Node/Literal

## PyTransforms
#### _URLHash_
From column: _URL_
``` python
return  "malware/" + SM.md5_hash(getValue("URL"))
```


## Selections

## Semantic Types
| Column | Property | Class |
|  ----- | -------- | ----- |
| _Country_ | `schema:countryOfOrigin` | `memex:Malware1`|
| _Firstseen (UTC)_ | `memex:observedDate` | `memex:Malware1`|
| _Malware_ | `schema:name` | `memex:Malware1`|
| _Registrar_ | `memex:registrar` | `memex:IPAddress1`|
| _URLHash_ | `uri` | `memex:Malware1`|
| _Values_ | `schema:name` | `memex:IPAddress1`|
| _Values_ | `memex:autonomousSystemNumber` | `memex:IPAddress1`|


## Links
| From | Property | To |
|  --- | -------- | ---|
| `memex:Malware1` | `memex:hostedAt` | `memex:IPAddress1`|
