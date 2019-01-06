## Table of contents

*   [Getting started](#getting-started)

## Getting started

* SDK supports iOS 9.0
* SDK supports Swift Swift 4.2

### 1. Obtaining token
SDK requires token for starting initialization. [Token generation guide](https://github.com/idenfy/Documentation/blob/master/pages/GeneratingIdentificationToken.md)

### 2. Providing permissions
 `NSCameraUsageDescription'must be provided in the application's 'Info.plist' file:

```xml
<key>NSCameraUsageDescription</key>
<string>Required for document and facial capture</string>
```

### 3. Adding the SDK dependency
```ruby
pod 'iDenfySDK'
```

Run `pod install` to get the sdk.

### 4. Starting the flow