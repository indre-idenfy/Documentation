# Generate identification report

This endpoint lets you get report in pdf about identification.

### Report contains:
- Identification data
- Identification status
- Miscellaneous data
- AML data
- LID data
- Face photo
- Document photos

### Sending request
Send a *HTTP Post* request to: `https://ivs.idenfy.com/api/v2/generate-pdf/`

The request must contain *basic auth* headers where *username* is *api key* and *password* is *api secret*.<br>
The request must contain JSON with parameter:

|     Key    | Required |              Explanation              |   Type   |                                     Constraints<img width=/>                                     |
| -----------| -------- | ------------------------------------- | -------- | ------------------------------------------------------------------------------------------------ |
| `scanRef`  | Yes      | A unique string identifying a client identification. | `String` | -                                                                                 |

#### Response
For successful API call you get a pdf file in bytes and a response with a positive **200** status.


### Examples
#### Example request

```json
{
	"scanRef": "350e2420-8850-11e9-baa5-309c231b1bac"	
}
```

