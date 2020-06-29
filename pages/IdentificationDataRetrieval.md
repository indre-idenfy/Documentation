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

## Full identification status

The endpoint returns a full status of the identification.

- Endpoint: https://ivs.idenfy.com/api/v2/full-status

### Response structure

Request HTTP body is in JSON format which is described in tables below:

|JSON key        |Type    |Constraints      |Explanation|
|----------------|--------|-----------------|-----------|
|`face_match_result`|`String`|- Max length 30  |An automatic face analysis result (decision made by an automated platform). Possible values:<br>- FACE_MATCH<br>- FACE_MISMATCH<br>- NO_FACE_FOUND<br>- TOO_MANY_FACES<br>- FACE_TOO_BLURRY<br>- FACE_UNCERTAIN<br>- FACE_NOT_ANALYSED<br>- FACE_ERROR<br>- AUTO_UNVERIFIABLE<br>- FAKE_FACE<br>[For value explanations refer to status vocabulary](https://github.com/idenfy/Documentation/blob/master/pages/Vocabulary.md#identification-status-values-vocabulary).|
|`document_validity`|`String`|- Max length 30  |An automatic document analysis result (decision made by an automated platform). Possible values:<br>- DOC_VALIDATED<br>- DOC_INFO_MISMATCH<br>- DOC_NOT_FOUND<br>- DOC_NOT_FULLY_VISIBLE<br>- DOC_NOT_SUPPORTED<br>- DOC_FACE_NOT_FOUND<br>- DOC_TOO_BLURRY<br>- DOC_FACE_GLARED<br>- MRZ_NOT_FOUND<br>- MRZ_OCR_READING_ERROR<br>- DOC_EXPIRED<br>- COUNTRY_MISMATCH<br>- DOC_TYPE_MISMATCH<br>- DOC_DAMAGED<br>- DOC_FAKE<br>- DOC_ERROR<br>- AUTO_UNVERIFIABLE<br>- DOC_NOT_ANALYSED<br>- DOC_NAME_ERROR<br>- DOC_SURNAME_ERROR<br>- DOC_EXPIRY_ERROR<br>- DOC_DOB_ERROR<br>- DOC_PERSONAL_NUMBER_ERROR<br>- DOC_NUMBER_ERROR<br>- DOC_DATE_OF_ISSUE_ERROR<br>- DOC_SEX_ERROR<br>- DOC_NATIONALITY_ERROR<br>[For value explanations refer to status vocabulary](https://github.com/idenfy/Documentation/blob/master/pages/Vocabulary.md#identification-status-values-vocabulary)|
|`manual_face_match_result`|`String`|- Max length 30  |A manual face analysis result (decision made by a human). Possible values are the same as  `face_match_result` field.         |
|`manual_document_validity`|`String`|- Max length 30  | A manual document analysis result (decision made by a human). Possible values are the same as `document_validity` field.|
|`client`|`Object`|- |Dictionary that contains the data of the client. [Refer to status table](#client-data-table).|
|`client_identity_document`|`Object`|- |Dictionary that contains the data of the client identity document. [Refer to status table](#client-identity-document-table).|
|`attempt_count`|`Int`|- |Count of how many times a client has tried to identify himself|
|`suspection_reasons`|`List`|- |A list of suspicion reasons constants (strings) indicating why identification was suspected. Possible values:<br>- FACE_SUSPECTED<br>- DOC_MOBILE_PHOTO<br>- DEV_TOOLS_OPENED<br>- DOC_PRINT_SPOOFED<br>- FAKE_PHOTO<br>- AML_SUSPECTION<br>- AML_FAILED<br>- LID_SUSPECTION<br>- LID_FAILED<br>- AUTO_UNVERIFIABLE<br>[For value explanations refer to status vocabulary](https://github.com/idenfy/Documentation/blob/master/pages/Vocabulary.md#identification-status-values-vocabulary).|
|`start_time`|`String`|- Format: YYYY-MM-DD MM:SS.ss|The time of  when a client starts the identification process.|
|`finish_time`|`String`|- Format: YYYY-MM-DD MM:SS.ss|The time of  when the final decision for automatic processing was made.|
|`review_time`|`String`|- Format: YYYY-MM-DD MM:SS.ss|The time of when the identification was reviewed|

### Client data table

|JSON key        |Type    |Constraints      |Explanation|
|----------------|--------|-----------------|-----------|
|`name`|`String`|- Min length 1<br>- Max length 100 |A name of a client. |
|`surname`|`String`|- Min length 1<br>- Max length 100 |A surname of a client. |
|`date_of_birth`|`String`|- Format: YYYY-MM-DD |Date of birth of a client. |
|`personal_id_number`|`String`|- Min length 1  |Personal/national number of a client. |
|`document_number`|`String`|- Min length 1 |Number of a client document.|
|`document_type`|`String`|- Max length 30  |Type of a client document.|
|`expiry_date`|`String`|- Format: YYYY-MM-DD MM:SS.ss|Date when client token will become invalid.|
|`nationality`|`String`|- Any country in alpha-2 code|Nationality of a client.|
|`date_of_issue`|`String`|- Format: YYYY-MM-DD |Date of issue of a client document. |
|`sex`|`String`|- Values:<br>&nbsp;&nbsp;&nbsp;&nbsp;-`M`<br>&nbsp;&nbsp;&nbsp;&nbsp;-`F` |Gender of a client. |
|`country`|`String`|- Any country in alpha-2 code |A default document country in alpha-2 code for a client. |
|`default_country`|`String`|- Any country in alpha-2 code |A predefined document country for a client by the partner. |
|`utility_address`|`String`|- Max length 255  |Client address provided by partner |

### Client identity document table

|JSON key        |Type    |Constraints      |Explanation|
|----------------|--------|-----------------|-----------|
|`doc_name`       |`String`|- Max length 100 |Client name parsed from the document.|
|`doc_surname`        |`String`|- Max length 100 |Client surname parsed from the document.|
|`doc_date_of_birth`  |`String`|- Max length 10  |Client date of birth parsed from the document.|
|`doc_expiry_date`    |`String`|- Max length 100 |Client document expiry date parsed from the document.|
|`doc_personal_code`  |`String`|- Max length 30  |Client personal code parsed from the document.|
|`doc_document_number`|`String`|- Max length 100 |Client document number parsed from the document.|
|`doc_sex`            |`String`|- Max length 6   |Client sex parsed from the document. Possible values:<br>- MALE<br>- FEMALE<br>- UNDEFINED|
|`doc_nationality`    |`String`|- Max length 2   |Client nationality parsed from the document. Returned value is an alpha-2 country code.|
|`doc_date_of_issue`  |`String`|- Max length 10  |Client date of issue parsed from the document.|
|`doc_license_categories`|`String`|- Max length 30  |Client driving license categories (classes) parsed from the document.|
|`doc_document_type`  |`String`|- Max length 30  |Document type to complete identification. Possible values:<br>- ID_CARD<br>- PASSPORT<br>- RESIDENCE_PERMIT<br>- DRIVER_LICENSE<br>- OTHER|
|`doc_country`        |`String`|- Max length 2   |Documents issuing country parsed from the document. Returned value is an alpha-2 country code.|
|`mrz_name`           |`String`|- Max length 100 |Client name read from the document MRZ.|
|`mrz_surname`        |`String`|- Max length 100 |Client surname read from the document MRZ.|
|`mrz_date_of_birth`  |`String`|-                |Client date of birth read from the document MRZ.|
|`mrz_expiry_date`    |`String`|-                |Client document expiry date read from the document MRZ.|
|`mrz_personal_code`  |`String`|- Max length 30  |Client personal code read from the document MRZ.|
|`mrz_document_number`|`String`|- Max length 100 |Client document number read from the document MRZ.|
|`mrz_sex`            |`String`|- Max length 6   |Client sex read from the document MRZ. Possible values:<br>- MALE<br>- FEMALE<br>- UNDEFINED|
|`mrz_nationality`    |`String`|- Max length 2   |Client nationality read from the document MRZ. Returned value is an alpha-2 country code.|
|`mrz_country`        |`String`|- Max length 2   |Client documents issuing country read from the document MRZ. Returned value is an alpha-2 country code.|
|`mrz_document_type`  |`String`|- Max length 1   |Document type to complete identification. Possible values:<br>- ID_CARD<br>- PASSPORT<br>- RESIDENCE_PERMIT<br>- DRIVER_LICENSE<br>- OTHER|
|`mrz_document_subtype` |`String`|- Max length 1 |Document subtype to complete identification. Possible values:<br>- ID_CARD<br>- PASSPORT<br>- RESIDENCE_PERMIT<br>- DRIVER_LICENSE<br>- OTHER|
|`mrz_optional_data`  |`String`|- Max length 100 |Document optional data.|
|`mrz_string`         |`String`|- Max length 100 |Whole read mrz string. |
|`mrz_date_of_issue`  |`String`|- Max length 10  |Client date of issue read from the document MRZ.|
|`manual_name`        |`String`|- Max length 100 |Manually entered client name.|
|`manual_surname`     |`String`|- Max length 100 |Manually entered client surname.|
|`manual_date_of_birth` |`String`|-              |Manually entered client date of birth.|
|`manual_expiry_date` |`String`|- Max length 100 |Manually entered client document expiry date.|
|`manual_personal_code` |`String`|- Max length 30|Manually entered client personal code.|
|`manual_document_number` |`String`|- Max length 100  |Manually entered client document number.|
|`manual_sex`         |`String`|- Max length 6   |Manually entered client sex.|
|`manual_nationality` |`String`|- Max length 2   |Manually entered client nationality.|
|`manual_document_type` |`String`|- Max length 30|Manually entered client document type.|
|`manual_date_of_issue` |`String`|- Max length 10|Manually entered client document date of issue.|
|`manual_country`     |`String`|- Max length 2   |Manually entered client documents issuing country.|
|`document_type`      |`String`|- Max length 30  |Client selected document type.||
|`manual_utility_address`|`String`|- Max length 255  |Manually entered client manual utility address.|
|`manual_utility_address_match`|`Bool`|-         |Manually entered client manual utility address match.

### Example of full identification status

This is an example JSON body.

```json
{
    "face_match_result": "FACE_MATCH",
    "document_validity": "DOC_VALIDATED",
    "manual_face_match_result": "FACE_MATCH",
    "manual_document_validity": "DOC_VALIDATED",
    "client": {
        "name": "John Tom",
        "surname": "Smith",
        "date_of_birth": "2000-06-29",
        "personal_id_number": "123456789",
        "document_number": "123456",
        "document_type": "ID_CARD",
        "expiry_date": "2021-06-29",
        "nationality": "LI",
        "date_of_issue": "2010-12-20",
        "sex": "M",
        "country": "LI",
        "default_country": null,
        "utility_address": null
    },
    "client_identity_document": {
        "doc_name": "JOHN TOM",
        "doc_surname": "SMITH",
        "doc_date_of_birth": "2000-06-29",
        "doc_expiry_date": "2021-06-29",
        "doc_personal_code": "123456789",
        "doc_document_number": "123456",
        "doc_sex": "M",
        "doc_nationality": "LI",
        "doc_date_of_issue": "2010-12-20",
        "doc_license_categories": "",
        "doc_document_type": "ID_CARD",
        "doc_country": "LI",
        "mrz_name": "JOHN TOM",
        "mrz_surname": "SMITH",
        "mrz_date_of_birth": "2000-06-29",
        "mrz_expiry_date": "2021-06-29",
        "mrz_personal_code": "123456789",
        "mrz_document_number": "123456",
        "mrz_sex": "M",
        "mrz_nationality": "LI",
        "mrz_country": "LI",
        "mrz_document_type": "",
        "mrz_document_subtype": "",
        "mrz_optional_data": "",
        "mrz_string": "P<LIESMITH<<JOHN<TOM<<<<<<<<<<<<<<<<<<<<<<<<<1234567897LIE0006297M2106294<<<<<<<<<<<<<<00",
        "mrz_date_of_issue": "2010-12-20",
        "manual_name": "JOHN TOM",
        "manual_surname": "SMITH",
        "manual_date_of_birth": "2000-06-29",
        "manual_expiry_date": "2021-06-29",
        "manual_personal_code": "123456789",
        "manual_document_number": "123456",
        "manual_sex": "M",
        "manual_nationality": "LI",
        "manual_document_type": "ID_CARD",
        "manual_date_of_issue": "",
        "manual_country": "LI",
        "document_type": "ID_CARD",
        "manual_utility_address": "",
        "manual_utility_address_match": null
    },
    "attempt_count": 2,
    "suspection_reasons": [],
    "start_time": "2020-06-26 09:54:32",
    "finish_time": "2020-06-26 09:54:34",
    "review_time": "2020-06-26 09:54:35"
}
```

