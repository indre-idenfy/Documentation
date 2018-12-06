# Identification result callback

When a client completes identification - your registered web hook endpoint will receive a HTTP POST request containing data and status of the identification.

Request HTTP body is in JSON format which is described in tables below:

|JSON key    |Type    |Constraints      |Explanation                                                                                                   |
|------------|--------|-----------------|--------------------------------------------------------------------------------------------------------------|
|`status`    |`Object`|-                |Dictionary that contains the status of the identification. [Refer to status table](#status-table).                                      |
|`data`      |`Object`|-                |Dictionary that contains parsed data from clients identity document. [Refer to data table](#data-table).                                          |
|`fileUrls`  |`Object`|-                |Dictionary that contains url links to download or view client's identification photos. [Refer to file urls table](#file-urls-table)                        |
|`aml`       |`Object`|-                |Dictionary that contains anti-money-laundering (AML) service data. Only applicable if AML is enabled for you. [Refer to AML documentation](). |
|`lid`       |`Object`|-                |Dictionary that contains lost-invalid-documents (LID) service data. Only applicable if LID is enabled for you. [Refer to LID documentation]().|
|`scanRef`   |`String`|- Max length 36  |A unique string to trace back an identification on iDenfy’s side.                                             |
|`clientId`  |`String`|- Max length 100 |A unique string to trace back a client on your side.                                                          |


### Status table

|JSON key        |Type    |Constraints      |Explanation|
|----------------|--------|-----------------|-----------|
|`overall`       |`String`|- Max length 30  |An overall status of the identification. It is a combination of manual and automatic verification results. Possible values:<br>- APPROVED<br>- DENIED<br>- SUSPECTED<br>- NOT_REVIEWED                                              |
|`autoFace`      |`String`|- Max length 30  |An automatic face analysis result (decision made by an automated platform). Possible values:<br>- FACE_MATCH<br>- FACE_MISMATCH<br>- NO_FACE_FOUND<br>- TOO_MANY_FACES<br>- FACE_TOO_BLURRY<br>- FACE_ERROR<br>- AUTO_UNVERIFIABLE  |
|`manualFace`    |`String`|- Max length 30  |A manual face analysis result (decision made by a human). Possible values are the same as  `autoFace` field.                                                                                                                        |
|`autoDocument`  |`String`|- Max length 30  |An automatic document analysis result (decision made by an automated platform). Possible values:<br>- DOC_VALIDATED<br>- DOC_INFO_MISMATCH<br>- DOC_NOT_FOUND<br>- DOC_NOT_SUPPORTED<br>- DOC_FACE_NOT_FOUND<br>- DOC_NAME_ERROR<br>- DOC_SURNAME_ERROR<br>- DOC_EXPIRY_ERROR<br>- DOC_DOB_ERROR<br>- DOC_PERSONAL_NUMBER_ERROR<br>- DOC_NUMBER_ERROR<br>- DOC_TOO_BLURRY<br>- MRZ_NOT_FOUND<br>- MRZ_OCR_READING_ERROR<br>- DOC_EXPIRED<br>- COUNTRY_MISMATCH<br>- DOC_ERROR<br>- AUTO_UNVERIFIABLE|
|`manualDocument`|`String`|- Max length 30  |A manual document analysis result (decision made by a human). Possible values are the same as `autoDocument` field.|

### Data table

|JSON key             |Type    |Constraints      |Explanation|
|---------------------|--------|-----------------|-----------|
|`docFirstName`       |`String`|- Max length 100 |Clients name parsed from the document.|
|`docLastName`        |`String`|- Max length 100 |Clients surname parsed from the document.|
|`docNumber`          |`String`|- Max length 15  |Clients document number parsed from the document.|
|`docPersonalCode`    |`String`|- Max length 15  |Clients personal code parsed from the document.|
|`docExpiry`          |`String`|- Max length 10  |Clients document expiry date parsed from the document.|
|`docDob`             |`String`|- Max length 10  |Clients date of birth parsed from the document.|
|`docType`            |`String`|- Max length 30  |Clients used document type to complete identification. Possible values:<br>- ID_CARD<br>- PASSPORT<br>- RESIDENCE_PERMIT<br>- DRIVER_LICENSE<br>- OTHER|
|`docSex`             |`String`|- Max length 10  |Clients sex parsed from the document. Possible values:<br>- MALE<br>- FEMALE<br>- UNDEFINED|
|`docNationality`     |`String`|- Max length 2   |Clients nationality parsed from the document. Returned value is an alpha-2 country code.|
|`docIssuingCountry`  |`String`|- Max length 2   |Clients documents issuing country parsed from the document. Returned value is an alpha-2 country code.|
|`selectedCountry`    |`String`|- Max length 2   |Clients selected country in identification platform. Returned value is an alpha-2 country code.|
|`manuallyDataChanged`|`Bool`  |-                |Indicates whether a manual reviewer has changed any parsed data from the document. Applicable only when a human reviews an identification. In automated verification response this value is `false`.|

### File urls table

|JSON key    |Type          |Constraints      |Explanation|
|------------|--------------|-----------------|-----------|
|`FRONT`     |`String (URL)`|- Max length 500 |An URL to download front document side photo with which a client has completed an identification.|
|`BACK`      |`String (URL)`|- Max length 500 |An URL to download back document side photo with which a client has completed an identification.|
|`FACE`      |`String (URL)`|- Max length 500 |An URL to download face photo with which a client has completed an identification.|
