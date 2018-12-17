# Identification data retrieval

You can additionally check a specific identification (photo urls, status, etc.)
Every of the endpoints below accept only one JSON parameter `scanRef` and require a basic auth header (**API key** and **API secret**).

Example JSON:
```json
{
  "scanRef":"scan-ref"
}
```

## Identification status

The endpoint returns an overall status of the identification.

- Endpoint: https://ivs.idenfy.com/api/v2/status

Returned response:

|JSON key        |Type    |Constraints      |Explanation|
|----------------|--------|-----------------|-----------|
|`status`        |`String`|- Max length 30  |An overall status of the identification. Possible values:<br>- APPROVED<br>- DENIED<br>- SUSPECTED<br>- REVIEWING<br>- ACTIVE<br>- EXPIRED<br>[For value explanations refer to status vocabulary](https://github.com/idenfy/Documentation/blob/master/pages/Vocabulary.md#identification-status-values-vocabulary).                                              |
|`scanRef`       |`String`|- Max length 36  |A unique string to trace back an identification on iDenfy’s side.                                             |
|`clientId`      |`String`|- Max length 100 |A unique string to trace back a client on your side.                                                          |


## Identification data

- Endpoint: https://ivs.idenfy.com/api/v2/data

## Identification file urls

- Endpoint: https://ivs.idenfy.com/api/v2/files

