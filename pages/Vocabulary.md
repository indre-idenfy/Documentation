# Vocabulary

## Common values vocabulary

|Value         |Meaning                                                              |
|---------------|---------------------------------------------------------------------|
|`clientId`     |A unique string identifying a client.                                |
|`scanRef`      |A unique string identifying a client identification in iDenfy’s side.| 


## Identification status values vocabulary

|Value                        |Explanation                                     |
|-----------------------------|------------------------------------------------|
|`APPROVED`                   |Identification was successful and approved by an automated platform or a manual reviewer.|
|`DENIED`                     |Identification was not successful and was denied by an automated platform or a manual reviewer.|
|`SUSPECTED`                  |Identification seemed fraudulent for an automated platform so it was immediately terminated.|
|`REVIEWING`                  |Client has selected 'Other Documents'. With this type of identification an automatic verification is not possible therefore it is being reviewed by a human. 'Other Documents' type may be not applicable to you. Contact iDenfy support to turn this feature on or off.|
|`EXPIRED`                    |A token associated with this identification got expired and an identification process never took place (token was not used).|
|`ACTIVE`                     |An identification has no decisive status. A token representing this identification was not used and is still active and can be used by a client any moment.|
|`FACE_MATCH`                 |Selfie face matched face from the identity document.|
|`FACE_MISMATCH`              |Selfie face did not match face from the identity document.|
|`NO_FACE_FOUND`              |No faces could be found in the selfie photo.|
|`TOO_MANY_FACES`             |Too many faces found in the selfie photo.|
|`FACE_TOO_BLURRY`            |Selfie face was too blurry and face matching could not be performed.|
|`FACE_ERROR`                 |Unclassified error happened when locating/matching faces.|
|`FACE_NOT_ANALYSED`          |Identification was denied for some other reason e.g. it was suspected therefore face analysis was not performed.|
|`FAKE_FACE`                  |Selfie face looks not real.|
|`DOC_VALIDATED`              |Document was successfully analysed and approved.|
|`DOC_INFO_MISMATCH`          |When generating token provided data mismatched with the data parsed from the document.|
|`DOC_NOT_FOUND`              |Document could not be found in the photo.|
|`DOC_NOT_SUPPORTED`          |A client has tried to identify himself with an unsupported document.|
|`DOC_FACE_NOT_FOUND`         |A face in the document could not be located.|
|`DOC_NAME_ERROR`             |In the front side of the document a name field could not be found or parsed.|
|`DOC_SURNAME_ERROR`          |In the front side of the document a surname field could not be found or parsed.|
|`DOC_EXPIRY_ERROR`           |In the front side of the document a document expiry date field could not be found or parsed.|
|`DOC_DOB_ERROR`              |In the front side of the document a date of birth field could not be found or parsed.|
|`DOC_PERSONAL_NUMBER_ERROR`  |In the front side of the document a personal code field could not be found or parsed.|
|`DOC_NUMBER_ERROR`           |In the front side of the document a document number field could not be found or parsed.|
|`DOC_TOO_BLURRY`             |Document looks too blurry in the photo and data parsing can not be performed.|
|`MRZ_NOT_FOUND`              |Machine Readable Zone (MRZ) could not be located.|
|`MRZ_OCR_READING_ERROR`      |Failed to read and parse Machine Readable Zone (MRZ). Possibly check-digit discrepancy.|
|`DOC_EXPIRED`                |Document is expired and identification on this document can not be performed.|
|`COUNTRY_MISMATCH`           |Selected country and identity document issuing country do not match.|
|`DOC_ERROR`                  |Unclassified error happened while analysing identity document.|
|`DOC_NOT_ANALYSED`           |Identification was denied for some other reason e.g. it was suspected therefore document analysis was not performed.|
|`DOC_DAMAGED`                |Document is damaged or cracked therefore no logner valid.|
|`DOC_FAKE`                   |Document is forged therefore invalid.|
|`AUTO_UNVERIFIABLE`          |This identification can not be automatically verified and needs to be verified by human.|
|`FACE_SUSPECTED`             |Automatic algorithms triggered a suspicion that selfie face is not genuine.|
|`DOC_MOBILE_PHOTO`           |A photo of a document is shown from a mobile screen.|
|`DEV_TOOLS_OPENED`           |A client performing identification has opened dev-tools in the browser.|
|`DOC_PRINT_SPOOFED`          |Automatic algorithms triggered a suspicion that document is printed on paper.|
|`FAKE_PHOTO`                 |General identifier for a fake photo.|
|`AML_SUSPECTION`             |If AML functionality is turned on for you - this reason specifies that a client is in PEPs or Sanctions list.|
|`AML_FAILED`                 |If AML functionality is turned on for you - this reason specifies that the check has failed.|
|`LID_SUSPECTION`             |If LID functionality is turned on for you - this reason specifies that client's document is found in lost or stolen documents database.|
|`LID_FAILED`                 |If LID functionality is turned on for you - this reason specifies that the check has failed.|
|`UNDER_AGE`                  |An age read from document is lower than partner age limit.|
|`UNKNOWN_AGE`                |Partner given age limit but age from document was not read.|
|`NAME`                       |Partner given client name does not match one read form document.|
|`SURNAME`                    |Partner given client surname does not match the one read form document.|
|`DOCUMENT_NUMBER`            |Partner given client document number does not match the one read form document.|
|`PERSONAL_CODE`              |Partner given client personal code does not match the one read form document.|
|`EXPIRY_DATE`                |Partner given client expiry date does not match the one read form document.|
|`DATE_OF_BIRTH`              |Partner given client date of birth does not match the one read form document.|
|`DATE_OF_ISSUE`              |Partner given client date of issue does not match the one read form document.|
|`FULL_NAME`                  |Partner given client full name does not match the one read form document.|

