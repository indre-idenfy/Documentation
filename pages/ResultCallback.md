# Identification result callback

When a client completes identification - your registered web hook endpoint will receive a HTTP POST request containing data and status of the identification.

Request HTTP body is in JSON format which is described in tables below:

|JSON key    |Type    |Constraints      |Explanation                                                                            |
|------------|--------|-----------------|---------------------------------------------------------------------------------------|
|`status`    |`Object`|-                |Dictionary that contains the status of the identification e.g. APPROVED.               |
|`data`      |`Object`|-                |Dictionary that contains parsed data from clients identity document.                   |
|`fileUrls`  |`Object`|-                |Dictionary that contains url links to download or view client's identification photos. |
|`aml`       |`Object`|-                ||
|`lid`       |`Object`|-                ||
|`scanRef`   |`String`|- Max length 36  ||
|`clientId`  |`String`|- Max length 100 ||


### Status table

|JSON key    |Type    |Constraints      |Explanation|
|------------|--------|-----------------|-----------|
|            |        |                 |           |

### Data table

|JSON key    |Type    |Constraints      |Explanation|
|------------|--------|-----------------|-----------|
|            |        |                 |           |

### File urls table

|JSON key    |Type    |Constraints      |Explanation|
|------------|--------|-----------------|-----------|
|            |        |                 |           |
