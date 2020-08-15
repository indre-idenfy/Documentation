# Video call service

You can generate video call token and record video call.

## Create video call

This endpoint lets you create video call token for video or photos identifications.

### Sending request
Send a *HTTP Post* request to: [https://ivs.idenfy.com/api/v2/video-call](https://ivs.idenfy.com/api/v2/video-call) <br>
The request must contain *basic auth* headers where *username* is *api key* and *password* is *api secret*.<br>
Client should be already created, otherwise generate new token with token type *VIDEO_CALL* or *VIDEO_CALL_PHOTO* <br>
The request must contain JSON with these parameters:

|     Key    | Required |              Explanation              |   Type   |                                     Constraints<img width=/>                                     |
| -----------| -------- | ------------------------------------- | -------- | ------------------------------------------------------------------------------------------------ |
| `scanRef`  | Yes      | A unique string identifying a client identification.                  | `String` | -                                                                                                |
| `photos`   | No       | Indicates whether photos of client and document should be taken.| `Bool` | - |

### Examples
#### Example request for video call endpoint to make a video call photo token

```json
{
    "scanRef": "unique_scan_ref",
    "photos": true
}
```
#### Example request for video call token

```json
{
    "scanRef": "unique_scan_ref"
}
```

#### Example responses
Successful API call returns json response with url which redirects to video call.

## Video call record

This endpoint lets you retrieve video call photos and video.

### Sending request
Send a *HTTP Post* request to: [https://ivs.idenfy.com/api/v2/video-call-record](https://ivs.idenfy.com/api/v2/video-call-record) <br>
The request must contain JSON with these parameters:

|     Key    | Required |              Explanation              |   Type   |                                     Constraints<img width=/>                                     |
| -----------| -------- | ------------------------------------- | -------- | ------------------------------------------------------------------------------------------------ |
| `scanRef`  | Yes      | A unique string identifying a client identification. | `String` | -                                                                                                |

### Examples
#### Example request 

```json
{
    "scanRef": "unique_scan_ref"
}
```

#### Example responses
Successful API call returns json response with photos and video urls.
```json
{
    "photos": {
        "VIDEO_CALL_BACK": "http://this-is-a-document-back-photo-url",
        "VIDEO_CALL_FACE": "http://this-is-a-face-photo-url",
        "VIDEO_CALL_FRONT": "http://this-is-a-document-front-photo-url"
    },
    "videos": [
         "http://this-is-a-identification-video-url"
    ]
}
```

## Video call callabck

When a client completes video call - your registered web hook endpoint will receive a HTTP POST request containing data and status of the video call.

Your API **must** return HTTP response with status code `200`. Otherwise a client will see a failed identification message and will be redirected to a fail url.

### Callback structure

Request HTTP body is in JSON format:

|JSON key    |Type    |Constraints      |Explanation                                                                                                   |
|------------|--------|-----------------|--------------------------------------------------------------------------------------------------------------|
|`videoCallAnswers`|`String`| -         |Dictionary that contains questions and answers with success indicators.                                      |
|`date`      |`String`|-                |Video call creation time.                                                                                     |
|`status`    |`Bool`  |-                |Status of the video call. Possible values:<br>- *true* - indicates success<br>- *false* - indicates failure.                                        |
|`scanRef`   |`String`|-                |A unique string identifying a client identification.                                                          |
|`authToken` |`String`|-                |A unique string for identification process.                                                                  |
|`clientId`  |`String`|-                |A unique string identifying a client on your companies side.                                                  |

### Examples

This is an example JSON body in the callback HTTP request.

```json
{
    "videoCallAnswers": {
        "Question 1": {
            "answer": "Answer to first question.",
            "correct": true
        }, 
        "Question 2": {
            "answer": "Answer to second question.", 
            "correct": true
        }
    },
    "date": "2020-08-14 12:48:08.085275+00:00", 
    "status": true,
    "scanRef": "unique_scan_ref", 
    "authToken": "unique_auth_token",
    "clientId": "unique_client_id"
}
```
