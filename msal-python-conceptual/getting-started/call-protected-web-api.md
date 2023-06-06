# Call a protected web API

## Using the token

Getting a token is not a goal per se. It's a necessary step to call a protected API. The token needs to be used to access a Web API. The way to do it is by setting the Authorization header to be "Bearer", followed by a space, followed by the access token.

## Using the access token to call a protected Web API

Note that the code below shows how to call directly the web API with Requests. You can also use libraries which will only require the access token (DocumentDb for instance) and will take care of the headers details. In practice the code might change depending on the libraries you want to use.

```python
endpoint = "url to the API"
http_headers = {'Authorization': 'Bearer ' + result['access_token'],
               'Accept': 'application/json',
               'Content-Type': 'application/json'}
data = requests.get(endpoint, headers=http_headers, stream=False).json()
```
