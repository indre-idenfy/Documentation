## Table of contents

*   [Getting started](#getting-started)
*   [Callbacks](#callbacks)
*   [Customising flow](#customising-flow)
*   [UI Customisation](#ui-customisation)

## Getting started
The SDK supports API Level 15 and above

Our current gradle configuration supports newest support library:

`targetSdkVersion = 28`

`compileSdkVersion = 28`

`buildToolsVersion '28.0.3'`

### 1. Obtaining token
SDK requires token for starting initialization. [Token generation guide](https://github.com/idenfy/Documentation/blob/master/pages/GeneratingIdentificationToken.md)

### 2. Adding the SDK dependency
In the root level (project module) gradle add following implementation:

```gradle
repositories {
  ...
  maven {
    url  "https://dl.bintray.com/idenfy/idenfy"
  }
}
```
In the app level gradle add following implementation:
```gradle
repositories {
  ...
  dependencies {  
      implementation 'idenfySdk:com.idenfy.idenfySdk:1.0.7' 
    }
}
```

### 4. Configuring SDK
It is required to provide following configuration:
### Java
```java
IdenfySettings idenfySettings = new IdenfySettings.IdenfyBuilder()
                .withAuthToken("AUTH_TOKEN")
                .build();
```
### 5. Presenting Activity

Instance of IdenfyController is required for starting a flow.

### Java
```java
   IdenfyController.getInstance().startActivityForResult(this, IdenfyController.IDENFY_REQUEST_CODE, idenfySettings);
```
## Callbacks
SDK provides following callbacks: onSuccess, onError and onUserExit.

It is required to override onActivityResult for receiving responses.

### Java
```java
    @Override
    protected void onActivityResult(int requestCode, int resultCode, Intent data) {
        super.onActivityResult(requestCode, resultCode, data);
        if (requestCode == IdenfyController.IDENFY_REQUEST_CODE) {

            if (resultCode == IdenfyController.AUTHENTICATION_RESULT_CODE) {
                AuthenticationResultResponse authenticationResultResponse = data.getParcelableExtra(IdenfyController.ON_AUTHENTICATION_RESULT);
            } else if (resultCode == IdenfyController.ERROR_CODE) {
                IdenfyErrorResponse idenfyErrorResponse = data.getParcelableExtra(IdenfyController.ON_ERROR);
                //Error response
            } else if (resultCode == IdenfyController.USER_EXIT_CODE) {
                //User exited the SDK
            }
            
        }
    }
```

[Additional information about callbacks](https://github.com/idenfy/Documentation/blob/master/pages/StandardErrorMessages.md)

## Customising flow
 SDK provides various options for changing identification flow. All requirements can be specified inside of IdenfyBuilder()

 
