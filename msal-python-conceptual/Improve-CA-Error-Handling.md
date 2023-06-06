Improve CA Error Handling
=========================

Problem Statement
-----------------

...

Usage Pattern Example
---------------------

This is a sequence of calls that an app might make to take advantage of classification. This hypothetical app downloads a set of documents from various cloud endpoints and displays document thumbnails in a list. For documents that cannot be downloaded, the app makes decision on how to paint the UI, depending on the classification of the error condition. This is a very simplified example, written in pseudo code. It assumes that each document is downloaded from a different cloud endpoint that requires a different access token. This will, of course, be much more complicated in reality.

```python
for documentUrl in documentUrls:
    authParams = getAuthParams()
    authParams.scope = getScopeFromUrl(documentUrl)
    authResult = msal_app.acquire_token_silently(authParams)
    if authResult:
        if "error" not in authResult:
            document = downloadDocument(authenticationToken, documentUrl)
            showDocumentThumbnail(document)
        elif authResult.get("classification") == "basic_action":
            # Show the button that invokes AcquireTokenInteractively()
            showFixItButton()
        elif authResult.get("classification") == "additional_action":
            # Show a message that explains to the user that fixing the problem is more involved.
            showAdditionalActionMessage();
            # Show the button that invokes AcquireTokenInteractively()
            showFixItButton()
        elif authResult.get("classification") == "message_only":
            # Do nothing here. Skip documents that cannot be downloaded at this time.
            pass
        else:
            # Invoke default error handling routine that assumes no tokens can be issued, and no documents can be shown.
            # Hide all thumbnails and show a button to fix the issue.
            hideAllDocuments()
            showSignInMessage()
            showFixItButton()
            # Or, you could simply continue the loop
            # because the next document would not be affected by this document's error

```
