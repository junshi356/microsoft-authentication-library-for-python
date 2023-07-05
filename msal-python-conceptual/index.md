---
title: Microsoft Authentication Library (MSAL) for Python
description: "Get started with the Microsoft Authentication Library for Python to sign in users or apps with Microsoft identities."
---

# Microsoft Authentication Library (MSAL) for Python

Get started with the Microsoft Authentication Library for Python to sign in users or apps with Microsoft identities ([Azure AD](https://azure.microsoft.com/services/active-directory/), [Microsoft Accounts](https://account.microsoft.com) and [Azure AD B2C](https://azure.microsoft.com/services/active-directory-b2c/) accounts) and obtain tokens to call Microsoft APIs such as [Microsoft Graph](https://graph.microsoft.io/) or your own APIs registered with the [Microsoft identity platform](https://aka.ms/aaddevv2).

Follow steps to install the package and try out example code for basic tasks.

## Prerequisites

- An Azure account with an active subscription. [Create a free account][azure_sub].
- [Python 3.6+](https://www.python.org/downloads/).

## Install the package

Install the MSAL for Python package. You can find MSAL Python on [Pypi](https://pypi.org/project/msal/).
```Bash
pip install msal
```

## Setting up

Before using MSAL Python [register your application](/azure/active-directory/develop/quickstart-v2-register-an-app) with the Microsoft identity platform.

## Usage

Acquiring tokens with MSAL Python follows this 3-step pattern. This is the high level conceptual pattern. There will be some variations for different flows. They are demonstrated in the [runnable samples](https://github.com/AzureAD/microsoft-authentication-library-for-python/tree/dev/sample).

1. MSAL proposes a clean separation between [public client applications, and confidential client applications](https://tools.ietf.org/html/rfc6749#section-2.1). Therefore, create either a `PublicClientApplication` or a `ConfidentialClientApplication` instance, and reuse it during the lifecycle of your app. The following example shows a `PublicClientApplication`:

   ```python
   from msal import PublicClientApplication
   app = PublicClientApplication(
       "your_client_id",
       authority="https://login.microsoftonline.com/Enter_the_Tenant_Name_Here")
   ```

   Later, each time you would want an access token, you start by:
   ```python
   result = None  # It is just an initial value. Please follow instructions below.
   ```

2. The API model in MSAL provides you explicit control on how to utilize token cache. This cache part is technically optional, but we highly recommend you to harness the power of MSAL cache. It will automatically handle the token refresh for you.

   ```python
   # We now check the cache to see
   # whether we already have some accounts that the end user already used to sign in before.
   accounts = app.get_accounts()
   if accounts:
       # If so, you could then somehow display these accounts and let end user choose
       print("Pick the account you want to use to proceed:")
       for a in accounts:
           print(a["username"])
       # Assuming the end user chose this one
       chosen = accounts[0]
       # Now let's try to find a token in cache for this account
       result = app.acquire_token_silent(["your_scope"], account=chosen)
   ```

3. If there is no suitable token in the cache or you've chosen to skip the previous step, send a request to Azure AD to get a token. There are different methods based on your client type and scenario. Here we demonstrate a placeholder flow.

   ```python
   if not result:
       # So no suitable token exists in cache. Let's get a new one from Azure AD.
       result = app.acquire_token_by_one_of_the_actual_method(..., scopes=["User.Read"])
   if "access_token" in result:
       print(result["access_token"])  # Yay!
   else:
       print(result.get("error"))
       print(result.get("error_description"))
       print(result.get("correlation_id"))  # You may need this when reporting a bug
   ```

# Usage scenarios

MSAL Python can be used by applications to acquire tokens to access protected APIs. Tokens can be acquired by different **application types**: desktop applications, web applications, web APIs, and applications running on devices that don't have a browser (such as IoT devices). In MSAL Python, applications are categorized as follows:

- **Public client applications (desktop and mobile)**. These types of apps cannot store app secrets securely.
- **Confidential client applications (web apps, web APIs, and daemon applications)**. These type of apps securely store a secret registered with Azure AD.

Learn more about instantiating and configuring the above in the [Client applications](./client-applications.md) topic.

MSAL Python supports acquiring tokens either in the name of a user or in the name of the application itself (without a user). In the latter case, a confidential client application must be used.

MSAL Python can be used in applications running on different operating systems (Windows, Linux, macOS).

Key scenarios supported by MSAL Python:

- [Web application that signs in users](/azure/active-directory/develop/scenario-web-app-sign-user-overview)
- [Web Application signing in a user and calling a Web API in the name of the user](/azure/active-directory/develop/scenario-web-app-call-api-overview) (note that MSAL only helps the web application to sign in and obtain tokens. To [protect a web API](/azure/active-directory/develop/scenario-protected-web-api-overview), you will need other libraries).
- [Desktop application calling a Web API in the name of the signed-in user](/azure/active-directory/develop/scenario-desktop-overview)
- [Desktop/service daemon application calling Web API without a user](/azure/active-directory/develop/scenario-daemon-overview)
- [Application without a browser, or IOT application calling an API in the name of the user](/azure/active-directory/develop/scenario-desktop-acquire-token?tabs=python#command-line-tool-without-web-browser)

Can't find the scenario you are looking for? Check out the [supported scenarios and platforms](/azure/active-directory/develop/authentication-flows-app-scenarios#scenarios-and-supported-platforms-and-languages) across MSAL libraries.