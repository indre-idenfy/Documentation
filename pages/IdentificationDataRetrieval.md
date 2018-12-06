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

|Endpoint                            |
|------------------------------------|
|https://ivs.idenfy.com/api/v2/status|

## Identification data

|Endpoint                            |
|------------------------------------|
|https://ivs.idenfy.com/api/v2/data  |

## Identification file urls

|Endpoint                            |
|------------------------------------|
|https://ivs.idenfy.com/api/v2/files |

