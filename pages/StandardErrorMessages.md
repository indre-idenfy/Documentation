# Standard API errors

When interacting with iDenfy API you may encounter error responses. This means that you have tried to do an action which is not allowed or malformed in some way.

A standard error response has a HTTP status code 400 and a JSON body which:

|JSON key      |Explanation                                                                                                 |
|--------------|------------------------------------------------------------------------------------------------------------|
|`identifier`  |A constant indicating a type of error. Never changes, therefore can be used in code to automate processes. For possible values see the table below.  |
|`message`     |A human readable message describing an error. Mainly used for programers to get a clue of what went wrong.  |

### Error identifier constants

A list of error constants and their explanations.

|Error identifier          |Explanation                                                            |
|--------------------------|-----------------------------------------------------------------------|
|`INTERNAL_ERROR`          |Unhandled unknown internal error at *iDenfy* API side.                 |
|`BAD_VALUE`               |Supplied value is not valid.                                           |
|`MISSING_VALUE`           |Expected a supplied value but got none.                                |
|`UNAUTHORIZED`            |Missing Api key/secret in HTTP headers or Api key/secret not valid.    |
|`ENCODING_ERROR`          |Failed to encode/decode object.                                        |
|`JSON_ERROR`              |Malformed JSON body.                                                   |
|`TOKEN_NOT_VALID`         |Identification token is not valid or expired.                          |
|`PARTNER_CONTRACT_ERROR`  |A partner can not do a requested action because of the signed contract.|
|`METHOD_NOT_ALLOWED`      |Wrong HTTP method.                                                     |
