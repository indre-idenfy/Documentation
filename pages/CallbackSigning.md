# Callback signing

Callback signing is a simple method to secure your callback endpoints from
foreign requests.

To check webhook callbacks you need to compute SHA-256 HMAC of the whole HTTP body content 
with API secret as a key, and compare that with `Idenfy-Signature` header.

**Note**: You should not use standard `==` operator to avoid timing attacks. You
should use `hmac.compare_digest`, `crypto.timingSafeEqual`  or equivalent constant time string comparison.

### Examples

##### Python example

```python
import hmac

API_SECRET = "Agegb..." 

@app.route('/idenfy-callback')
def callback():
    signature = hmac.new(
        API_SECRET.encode(),
        request.get_data(),
        "sha256"
    ).hexdigest()
    
    request_signature = request.headers.get("Idenfy-Signature")
    
    if request_signature:
        if hmac.compare_digest(signature, request_signature):
            handle_request(request)
```

##### Javascript example

```javascript
const API_SECRET = "Agegb...";

function verifyPostData(req, res, next) {
    const payload = JSON.stringify(req.body)
    
    if (!payload) {
      return next('Request body empty.')
    }

    const hmac = crypto.createHmac('sha256', API_SECRET)
    const digest = Buffer(hmac.update(payload).digest('hex'))
    const checksum = Buffer(req.headers['idenfy-signature'])
    
    if (!checksum || !digest || !crypto.timingSafeEqual(checksum, digest)) {
        return next(`Request body digest (${digest}) did not match Idenfy-Signature (${checksum}).`)
    }
    
    return next()
}
```
