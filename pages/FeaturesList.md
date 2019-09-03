# iDenfy features list

This is the complete list of iDenfy supported features ranging from *document/face
scanning* to *api integration*.

---

### Administration platform
We provide an administration platform for observing identifications and statistics.

---

- #### Colleague account registration
You can register your colleagues to administration platform.

- #### Identification account configuration
You can configure colors, web-hooks, emails addresses and other 
identification account features.

- #### Identification list generation
You can filter and generate a list of identifications into various 
formats (e.g. txt, csv).

- #### Identification listing and search
You can observe identifications in real time and and search for 
specific ones by applying various filters.

- #### Identification token generation
You can generate identification urls, then copy and send them to your clients
without needing to integrate our API.

- #### PDF generation
You can generate a PDF report for any identification.

- #### Success rates and statistics 
You can observe various statistics and success rates by applying various
filters.

---

### Identification Api
We expose a rest API which can be called to retrieve identification tokens and
redirect your clients to identification platforms.

---

- #### Additional data retrieval
You can retrieve any identification's data 
(identification photos, document parsed data, analysis results, etc.).

- #### Callback body HMAC security header
To enhance communication security between your system and iDenfy's API
we provide a security header in a callback request.

- #### Delete identification data
You can choose to delete any identification data stored on iDenfy servers.

- #### Direct processing
You can choose not to use our UI platform and submit identification photos directly.

- #### IP whitelisting
To enhance communication security between your system and iDenfy's API
we provide a list of IPs which should be whitelisted on you platform.

- #### SSL encrypted traffic
Our all servers use SSL certificates enabling https traffic. 

- #### Storing identification data
We store identification data on our servers as long as needed.

---

### Constraints
You can specify constraints on how a platform or a user must behave. 

---

- #### Allowed document types
You can specify allowed document types e.g. only id card and passport.

- #### Countries blacklist
You can blacklist countries so people from those countries would not be
able to interact with iDenfy platform.

- #### Mandatory document fields
You can specify which document fields are essential to you or your business.

---

### Document scanning
We provide automatic algorithms that detect documents and parse their data.

---

- #### Document and client provided data comparison
We compare document read data with your provided data to ensure 
client authenticity.

- #### Document blur check
To ensure best OCR results we calculate overall document
blurriness.

- #### Document detection
Our algorithms automatically detect documents in provided photos.

- #### Document expiry validation
In document analysis process we check whether document is expired.

- #### Document face biometric data points
Our document face detection and recognition A.I. models place 168
biometric points on found document face for accurate face comparison.

- #### Document face blur detection
To ensure accurate face recognition we calculate overall 
found face blurriness.

- #### Document face detection
Our algorithms automatically detect documents' faces.

- #### Document face glare detection
To ensure accurate face recognition we calculate overall 
found face glare.

- #### MRZ check-digits validation
To ensure accurate MRZ reading we validate MRZ check-digits.

- #### MRZ reading
Our algorithms automatically can detect and read MRZs.

- #### Document template name and surname reading
Our algorithms automatically can detect and read name and surname from
a document's front side.

- #### Document template dates reading and validation
Our algorithms automatically can detect and read dates 
(such as *date of birth*, *expiry date*, *date of issue*) from
a document's front side. Additionally, dates are validated to ensure valid
format and logic.

- #### Document template nationality/issuing country reading and validation
Our algorithms automatically can detect and read nationality and 
issuing country from a document's front side. Additionally, 
nationality and issuing country are validated to ensure valid format and logic.

- #### Document template other fields reading
Additionally our algorithms can automatically detect and read:
*gender*, *document number*, *personal code*, *birth place*, 
*document authority*, *address*, *driver license categories*.

- #### Supported document types
Our algorithms support these document types: 
*id card*, *residence permit*, *passport*, *driver license*, *other*.

- #### Document template and mrz data comparison
To ensure accurate OCR reading and prevent counterfeits we compare 
template data with MRZ data.

- #### Utility bill analysis
We support utility bills. However, utility bills must be reviewed manually.

- #### Manual document review
We have a dedicated manual reviewing team which ensures that automatically 
read data from documents is accurate.

---

### Face scanning
We provide automatic algorithms that detect faces and does face comparison.

---

- #### Selfie face detection
Our algorithms can automatically detect selfie faces.

- #### Blurry selfie face detection
To ensure accurate face recognition and comparison we calculate overall
blurriness. If photo is too blurry, identification is automatically denied.

- #### More than one face detection
To comply with the law and ensure that a right face was compared we calculate
how many faces are visible in the photo. If there is more that one, identification
is automatically denied.

- #### Seflie face biometric data points
Our selfie face detection and recognition A.I. models place 168
biometric points on found selfie face for accurate face comparison.

---

### Fraud prevention

---

- #### Active liveness detection
- #### AML names check
- #### AML negative news check
- #### Background identification process video capturing
- #### Black and white printed document detection
- #### Document from mobile screen detection
- #### Document surface analysis for fake detection
- #### Fraud prevention api
- #### LID documents check
- #### Manual fraud prevention
- #### Passive document selfie detection
- #### Passive mobile screen selfie detection
- #### Screen pixels detection

---

### Mobile and Web 

---

- #### Android SDK
- #### Immediate redirect
- #### iOS SDK
- #### Mobile real time document scanning
- #### Mobile UI customization
- #### Redirect to success/error page
- #### Redirect to unverified page
- #### Showing custom support email
- #### Uploading photo
- #### Uploading utility bill
- #### Web iFrame
- #### Web UI customization
- #### Localisation

---

### Notifications

---

- #### Expired identification sessions
- #### Identification emails
- #### Identification callback endpoint
