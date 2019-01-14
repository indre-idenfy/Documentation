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



