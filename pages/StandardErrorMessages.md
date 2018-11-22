# Standard API errors

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