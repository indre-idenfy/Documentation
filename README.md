
# iDenfy API implementation
## Getting started
In order for you to start using our API you will need two things – ***API key*** and ***API secret***. Both can be retrieved by contacting *iDenfy support* or *iDenfy sales team*. Emails are given below:

|Email              |Position                       |
|-------------------|-------------------------------|
|sales@idenfy.com   |`Sales`                        |
|support@idenfy.com |`Support`                      |
|info@idenfy.com    |`Support`                      |

Also, you can visit [https://www.idenfy.com/start-trial/](https://www.idenfy.com/start-trial/) and fill up the form. Our team will contact you.
## Generating token
If you have ***API key*** and ***API secret*** you may now create an identification token.
### Sending request
Send a *HTTP Post* request to: [https://ivs.idenfy.com/api/v2/token](https://ivs.idenfy.com/api/v2/token)<br>
The request must contain JSON with optional and mandatory parameters:

|Key|Required|Explanation|Type|Constraints<img width=/>|Default value|
|-|-|-|-|-|-|
|`clientId`|Yes|A unique string identifying a client.|String|- Not null<br>- Max length 100<img width=750/>|-|
|`firstName`|No|A name(s) of a client to be identified.|String|- Min length 1<br>- Max length 100|-|
|`lastName`|No|A surname(s) of a client to be identified.|String|- Min length 1<br>- Max length 100|-|
|`successUrl`|No|An url where a client will be redirected after a successful identification.|String|- Min length 5<br>- Max length 2048|`https://`<br>`ui.idenfy.com/`<br>`result?status=success`|
|`errorUrl`|No|An url where a client will be redirected after a failed identification.|String|- Min length 5<br>- Max length 2048|`https://`<br>`ui.idenfy.com/`<br>`result?status=fail`|
|`locale`|No|A country code in alpha-2 format. Determines what default language a client will see in identification UI.|String|- Values:<br>&nbsp;&nbsp;&nbsp;&nbsp;-`lt`<br>&nbsp;&nbsp;&nbsp;&nbsp;-`en`<br>&nbsp;&nbsp;&nbsp;&nbsp;-`ru`|`en`|
|`expiryTime`|No|Length of time in seconds after which a newly generated token will become invalid.|Integer|- More than 0|`3600`|
|`sessionLength`|No|Length of time in seconds where a client is given to identify himself in indentification UI.|Integer|- More than 60<br>- Less than 3600|`600`|
|`country`|No|A default document country in alpha-2 code for a client. A client will not be able to select a different country.|String|- Any country in alpha-2 code|`null`|
### Receiving response
|Key|Explanation|Constraints|Example value|
|-|-|-|-|
|`message`|A message for a developer about the status of generated token.|- Max length 100<img width=375/>|`"Token created successfully"`
|`authToken`|A unique string for identification process (will be passed as an url parameter when redirecting a client to identification platform).|- Length equals 26|`"3FA5TFPA2ZE3LMPGGS1EGOJNJE"`
|`scanRef`|A unique string identifying a client identification in iDenfy’s side.|- Length equals 36|`"d2714c8a-ec05-11e8-834f-067891e3383a"`
|`clientId`|A unique string identifying a client in your companies side. (The same value when requesting to generate a token)|- More than 60<br>- Less than 3600|`“5F7E4FR14”`

### Graphical representation of token generation (UML activity)

![](https://raw.githubusercontent.com/idenfy/Documentation/master/iDenfy%20documentation.jpg =550x)

### Examples
#### Example requests

You can choose not to send any data regarding your client that needs to be identified. The only mandatory parameter is **clientId**.
```json 
{
"clientId": "100000"
}
```
As our only mandatory parameter is **clientId**, howerver we strongly recommend that you would append at least client’s name and surname if possible. It increases the success rate of identification verification.
```json
{
"clientId": "100000",
“firstName”: “John Tom”,
“lastName”: “Smith ”
}
```
Specify all of the parameters for full control.
```json
{
"clientId": "100000",
“firstName”: “John Tom”,
“lastName”: “Smith ”,
“successUrl”: “https://www.my-company.com/idenfy/success”,
“errorUrl”: “https://www.my-company.com/idenfy/fail”,
“locale”: “en”,
“expiryTime”: 600,
“sessionLength”: 600,
“country”: “en”
}
```
