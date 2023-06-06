## Instantiating an Application

### Pre-requisites

Before instantiating your app with MSAL Python,
1. Understand the types of Client applications available- [Public Client and Confidential Client applications](https://docs.microsoft.com/en-us/azure/active-directory/develop/msal-client-applications).
1. You'll need to [register](https://docs.microsoft.com/en-us/azure/active-directory/develop/quickstart-register-app) the application with Azure AD. You will therefore know:
    - Its `client_id` (a string representing a GUID)
    - The identity provider  URL (named the instance) and the sign-in audience for your application. These two parameters are collectively known as the authority.
    - Possibly the `Tenant+id` in the case you are writing a line of business application (just for your organization, also named single-tenant application)
    - In case it's a confidential client app, its application secret (`client_secret` string) or certificate
    - For web apps, you'll have also set the `redirect_uri` where the identity provider will contact back your application with the security tokens.

### Instantiating a Public Client application

```
app = msal.PublicClientApplication(
    config["client_id"],
    authority=config["authority"],
    )
```

### Instantiating a Confidential Client application

```
app = msal.ConfidentialClientApplication(
        config["client_id"],
        authority=config["authority"],
        client_credential=config["client_secret"],
        )
```
