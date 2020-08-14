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
#### Example request for video call photos identificatiohis endpoint lets you make a video call identification

```json
{
    "scanRef": "unique_scan_ref",
    "photos": true
}
```
#### Example request for video call identification

```json
{
    "scanRef": "unique_scan_ref"
}
```

#### Example responses
Successful API call returns json response with url which redirects to identification process.

## Video call record

This endpoint lets you retrieve video call photos and video if they were created.

### Sending request
Send a *HTTP Post* request to: [https://ivs.idenfy.com/api/v2/video-call-record](https://ivs.idenfy.com/api/v2/video-call-record) <br>
The request must contain JSON with these parameters:

|     Key    | Required |              Explanation              |   Type   |                                     Constraints<img width=/>                                     |
| -----------| -------- | ------------------------------------- | -------- | ------------------------------------------------------------------------------------------------ |
| `scanRef`  | Yes      | A unique string identifying a client identification.                  | `String` | -                                                                                                |

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
