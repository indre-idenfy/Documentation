# Python Flask example

## Case: redirecting to iDenfy platform

```python
# We are using this library to send HTTP requests.
import requests

# For this example we are using python Flask web-development framework.
from flask import Flask, redirect

# Init framework.
app = Flask(__name__)

# Your iDenfy account has an api key and api secret (credentials were provided for you by email).
MY_API_KEY = '4e8t4f487wrrew'
MY_API_SECRET = 'Tn78rwet41TCtq4VUq'

# Endpoint to call when generating identification token.
IDENFY_GENERATE_TOKEN_URL = 'https://ivs.idenfy.com/api/v2/token'
# Endpoint to redirect a user to with a generated token.
IDENFY_REDIRECT_URL = 'https://ivs.idenfy.com/api/v2/redirect'


# When a user comes to https://your-website/idenfy/kyc - he will be redirected to iDenfy platform.
@app.route('/idenfy/kyc')
def launch_identification() -> str:
    return redirect_to_idenfy()


def create_identification_token() -> str:
    # Create an identification token for your customer by sending a HTTP POST request to iDenfy platform.
    response = requests.post(
        url=IDENFY_GENERATE_TOKEN_URL,
        json=dict(clientId=1),
        auth=(MY_API_KEY, MY_API_SECRET)
    )

    response = response.json()
    return response['authToken']


def redirect_to_idenfy():
    # Redirect user to iDenfy platform with a newly generated identification token.
    return redirect(f'{IDENFY_REDIRECT_URL}?authToken={create_identification_token()}', code=301)


if __name__ == '__main__':
    app.run(host='127.0.0.1', port=10000)

```