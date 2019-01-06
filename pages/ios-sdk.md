## Table of contents

*   [Getting started](#getting-started)
*   [Callbacks](#callbacks)
*   [Customising Flow](#customising-flow)

## Getting started

* SDK supports iOS 9.0
* SDK supports Swift Swift 4.2

### 1. Obtaining token
SDK requires token for starting initialization. [Token generation guide](https://github.com/idenfy/Documentation/blob/master/pages/GeneratingIdentificationToken.md)

### 2. Providing permissions
 `NSCameraUsageDescription' must be provided in the application's 'Info.plist' file:

```xml
<key>NSCameraUsageDescription</key>
<string>Required for document and facial capture</string>
```

### 3. Adding the SDK dependency
```ruby
pod 'iDenfySDK'
```

Run `pod install` to get the sdk.

### 4. Configuring SDK

It is required to provide following configuration:

### Swift
```swift
 let idenfySettings = IdenfyBuilder()
    .withAuthToken("AUTH_TOKEN")
    .build()

    let idenfyController = IdenfyController(idenfySettings: idenfySettings)
```
### 5. Presenting ViewController

idenfyController instance is responsible for creating ViewController.
### Swift
```swift
   let idenfyVC = idenfyController.instantiateNavigationController()         

   self.present(idenfyVC, animated: true, completion: nil)
```
This code will present initial ViewController

## Callbacks
SDK provides following callbacks: onSuccess, onError and onUserExit.

Following method will provide callbacks from the SDK:

### Swift
```swift
    idenfyController.handleIDenfyCallbacks(
            onSuccess: { (AuthenticationResultResponse
                ) in
            }, 
            onError: { (IdenfyErrorResponse) in
            }, 
            onUserExit: {
                
            })
```

Alternatively each callback can be listened separately, by only calling particular closure.

 [Additional information about callbacks](https://github.com/idenfy/Documentation/blob/master/pages/StandardErrorMessages.md)

 ## Customising Flow
 SDK provides various options for changing identification flow. All requirements can be specified inside of IdenfyBuilder()

 ### 1. Setting documents country of issue

Following method will specify country of issue and will remove countries selection and terms of service UIViewController

```swift
   IdenfyBuilder()
    .withIssuingCountry("country_code")
    ...
```
Country code must be in alpha-2 code.


 ### 2. Removing initial ViewController

If default document country was selected during token generation the terms of services and country information View can be removed.

```swift
   IdenfyBuilder()
    .withPresentInitialView("country_code")
    ...
```
 ### 3. Custom locale

 By default SDK provides following translations:

 - English (en) GB
 - Polish (es) PL
 - Russian (es) RU


