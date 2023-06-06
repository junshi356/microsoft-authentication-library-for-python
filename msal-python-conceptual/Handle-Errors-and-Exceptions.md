## Errors and Exceptions in MSAL Python

### Most errors are conveyed as a return value

In MSAL Python, if an acquire token API call was unsuccessful, app developer is expected to handle such runtime error on the spot. So most errors are simply surfaced as the return value of each API call. That return value, as described in
[MSAL Python API Reference Doc](https://msal-python.readthedocs.io/en/latest/),
is a dictionary representing the json response from Microsoft Identity Platform:

* A successful response would contain `"access_token"` key, among others.
* An error response would contain `"error"` and usually `"error_description"`, among others.

The [format of these response is well defined in the industry standard OAuth2 protocol](https://tools.ietf.org/html/rfc6749#section-5).
In particular, when an error is returned, its `error_description` would contain a human-readable message, which in turn typically contains an
[Microsoft Identity Platform error code that is documented here](https://docs.microsoft.com/en-us/azure/active-directory/develop/reference-aadsts-error-codes).


### Exceptions are for something unexpected

MSAL Python would also raise `ValueError` exception when/if some input parameter(s) are malformed. Consider them as "compiling error" in static languages, that you would have to fix otherwise your app won't be able to run anyway. Other than that, MSAL Python might raise or relay some RuntimeError exceptions, but your app does not have to catch and handle them.
