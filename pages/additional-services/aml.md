# AML, PEP & Sanctions
This service checks whether given person is not in PEP or sanctions list.

#### Pricing
Please contact _iDenfy_ support for a detailed price-sheet.

#### Callback data
The service check returns data associated with the person under check in JSON format.
Overall response can be seen in the table below:

##### Overall response table

|JSON key          |Type        |Explanation                                                |
|------------------|------------|-----------------------------------------------------------|
|`status`          |`Object`    |The overall status of the service check.                   | 
|`data`            |`List`      |Data returned from services.                               |
|`serviceName`     |`String`    |The name of the service that was used to check a person.   |
|`serviceGroupType`|`String`    |The type of the service that was used. It is always `AML`. |
|`uid`             |`String`    |A unique identifier for a request. NOTE that it is unique only in one request scope. It is not unique globally. This parameter is only useful when doing multi-person checks.|
|`errorMessage`    |`String`    |In case of an error in the checking process a human readable error message is given.|

##### Status table

|JSON key            |Type        |Explanation                                                             |
|--------------------|------------|------------------------------------------------------------------------|
|`serviceSuspected`  |`Bool`      |Indicates whether a service found a record about the person under check.| 
|`checkSuccessful`   |`Bool`      |Indicated whether an error occurred while doing a check.                |
|`serviceFound`      |`Bool`      |Indicates whether a service was found for a given country.              |
|`serviceUsed`       |`Bool`      |Indicated whether a service was used.                                   |
|`overallStatus`     |`String`    |A mapping string indicating overall status of the check.                |

##### Data table
A service response in `data` field returns a list of objects which are detailed in the table below:

|JSON key            |Type        |Explanation                                                |
|--------------------|------------|-----------------------------------------------------------|
|`name`              |`String`    |The name of the person in the service's database.          | 
|`surname`           |`String`    |The surname of the person in the service's database.       |
|`nationality`       |`String`    |The nationality of the person in the service's database.   |
|`dob`               |`String`    |The date of birth of the person in the service's database. |
|`suspicion`         |`String`    |Tells the kind of the suspicion.                           |
|`reason`            |`String`    |Tells the reason of the kind of the suspicion.             |
|`score`             |`Integer`   |Confidence coefficient that the information about the person is true.|
|`lastUpdate`        |`String`    |Date of when the record was last updated.                  |
|`isPerson`          |`Bool`      |Indicates whether the record is about a person.            |
|`isActive`          |`Bool`      |Indicated whether a record is active.                      |

#### Example response

```json
{
    "status": {
        "serviceSuspected": true,
        "checkSuccessful": true,
        "serviceFound": true,
        "serviceUsed": true,
        "overallStatus": "SUSPECTED"
    },
    "data": [
        {
            "name": "NAME",
            "surname": "SURNAME",
            "reason": "LITHUANIA: GOVERNMENT - PRESIDENT",
            "nationality": "LITHUANIA",
            "dob": "1956",
            "suspicion": "PEPS",
            "score": 100,
            "lastUpdate": "2018-10-24",
            "isPerson": true,
            "isActive": true
        },
        {
            "name": "NAME",
            "surname": "SURNAME2",
            "reason": "LITHUANIA: GOVERNMENT - PRESIDENT",
            "nationality": "LITHUANIA",
            "dob": "1956",
            "suspicion": "PEPS",
            "score": 100,
            "lastUpdate": "2018-10-24",
            "isPerson": true,
            "isActive": true
        }
    ],
    "serviceName": "PilotApiAmlV2",
    "serviceGroupType": "AML",
    "uid": "OHT8GR5ESRF5XROWE5ZGCC49A",
    "errorMessage": null
}
```
