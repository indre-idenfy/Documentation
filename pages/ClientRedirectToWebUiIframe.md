# Client redirect to WEB UI

If you wish to have an iFrame implementation – there is a slightly different approach. You will have to directly insert identification platform url with **authToken** query string parameter into your iframe tag:

<center>

|UI platform url                       |
|--------------------------------------|
|https://ui.idenfy.com/                 |

|Query string parameter name           |Example value               |
|--------------------------------------|----------------------------|
|`authToken`                           |`3FA5TFPA2ZE3LMPGGS1EGOJNJE`|

</center>

***NOTE!*** 
When using iFrame locale parameter (when generating token) will have no effect. To force iFrame to use locale append `"lang=<alpha-2-country-code>"` url parameter. Example is given below.

***NOTE!*** 
If you are using our 3D-liveness feature with our iFrame solution, then the following changes have to be made before **October 21**. 
Starting from October 21, the liveness feature will not continue to work if your iFrame integration will not be updated.

The only required change is to add the following attribute to your iFrame element:
**allowfullscreen**


### Examples

An example redirect url:<br>https://ui.idenfy.com/?authToken=3FA5TFPA2ZE3LMPGGS1EGOJNJE

An example redirect url with english locale:<br>https://ui.idenfy.com/?authToken=3FA5TFPA2ZE3LMPGGS1EGOJNJE&lang=en

#### Example code

```html
<!DOCTYPE html>
<html>
  <body>
  
  <iframe 
    id='iframe' 
    allowfullscreen
    style="width:80%; height:800px;" 
    src="https://ui.idenfy.com/?authToken=3FA5TFPA2ZE3LMPGGS1EGOJNJE"
    allow="camera"
  ></iframe>
  
  <p id='display'></p>
  
  <script>
  window.addEventListener("message", receiveMessage, false);
    function receiveMessage(event) {
    console.log(event);
    // ...
  }
  </script>
  
  </body>
</html>
```
#### In message you can find data object where you can see these fields:

|Name        |Type    |Explanation|
|----------------|--------|-----------|
|`status`        |`String`|Identification status provided by an automated platform. Possible values:<br>- failed<br>- approved<br>                                              |
|`manualStatus`       |`String`|Identification status provided by manual reviewer. Possible values:<br>- null<br>- waiting<br>- failed<br>- approved<br>           
