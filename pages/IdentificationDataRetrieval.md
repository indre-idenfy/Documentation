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

## Full identification status

The endpoint returns a full status of the identification.

- Endpoint: https://ivs.idenfy.com/api/v2/full-status

Returned response:

|JSON key        |Type    |Constraints      |Explanation|
|----------------|--------|-----------------|-----------|
|`id`        	 |`String`|		    |A indentification's id. |
|`face_match_result`|`String`|- Max length 36  |An automatic face analysis result (decision made by an automated platform). Possible values:<br>- FACE_MATCH<br>- FACE_MISMATCH<br>- NO_FACE_FOUND<br>- TOO_MANY_FACES<br>- FACE_TOO_BLURRY<br>- FACE_UNCERTAIN<br>- FACE_NOT_ANALYSED<br>- FACE_ERROR<br>- AUTO_UNVERIFIABLE<br>- FAKE_FACE<br>[For value explanations refer to status vocabulary](https://github.com/idenfy/Documentation/blob/master/pages/Vocabulary.md#identification-status-values-vocabulary).  |
|`document_validity`|`String`|- Max length 100 |An automatic document analysis result (decision made by an automated platform). Possible values:<br>- DOC_VALIDATED<br>- DOC_INFO_MISMATCH<br>- DOC_NOT_FOUND<br>- DOC_NOT_FULLY_VISIBLE<br>- DOC_NOT_SUPPORTED<br>- DOC_FACE_NOT_FOUND<br>- DOC_TOO_BLURRY<br>- DOC_FACE_GLARED<br>- MRZ_NOT_FOUND<br>- MRZ_OCR_READING_ERROR<br>- DOC_EXPIRED<br>- COUNTRY_MISMATCH<br>- DOC_TYPE_MISMATCH<br>- DOC_DAMAGED<br>- DOC_FAKE<br>- DOC_ERROR<br>- AUTO_UNVERIFIABLE<br>- DOC_NOT_ANALYSED<br>- DOC_NAME_ERROR<br>- DOC_SURNAME_ERROR<br>- DOC_EXPIRY_ERROR<br>- DOC_DOB_ERROR<br>- DOC_PERSONAL_NUMBER_ERROR<br>- DOC_NUMBER_ERROR<br>- DOC_DATE_OF_ISSUE_ERROR<br>- DOC_SEX_ERROR<br>- DOC_NATIONALITY_ERROR<br>[For value explanations refer to status vocabulary](https://github.com/idenfy/Documentation/blob/master/pages/Vocabulary.md#identification-status-values-vocabulary). |
|`manual_face_match_result`|`String`|- Max length 30  |A manual face analysis result (decision made by a human). Possible values are the same as  `autoFace` field.                                                |
|`manual_document_validity`|`String`|- Max length 36  |A manual document analysis result (decision made by a human). Possible values are the same as `autoDocument` field. |
|`created`      |`Datetime`|		     |A datetime of when an identification was created. |
|`updated`      |`Datetime`|		     |A datetime of when an identification was updated. |
|`client`       |`Object`|		     |Dictionary that contains parsed data from clients. |
|`client_identity_document`|`Object`|		|Dictionary that contains parsed data from clients identity document.|
|`attempt_count`|`Int`|		     |A number of how many times a client has tried to identify himself.|
|`suspection_reasons`|`List`|- Max length 36  |A list of suspicion reasons constants (strings) indicating why identification was suspected. Possible values:<br>- FACE_SUSPECTED<br>- DOC_MOBILE_PHOTO<br>- DEV_TOOLS_OPENED<br>- DOC_PRINT_SPOOFED<br>- FAKE_PHOTO<br>- AML_SUSPECTION<br>- AML_FAILED<br>- LID_SUSPECTION<br>- LID_FAILED<br>- AUTO_UNVERIFIABLE<br>[For value explanations refer to status vocabulary](https://github.com/idenfy/Documentation/blob/master/pages/Vocabulary.md#identification-status-values-vocabulary). |
|`start_time`   |`Datetime`|		     |A datetime of when a client starts the identification process. |
|`finish_time`  |`Datetime`|		     |A datetime of when the final decision for automatic processing was made. |
|`review_time`  |`Datetime`|		     |A datetime of when the final decision for manual reviewing was made. |


## Identification data

- Endpoint: https://ivs.idenfy.com/api/v2/data

## Identification file urls

- Endpoint: https://ivs.idenfy.com/api/v2/files

