# MSAL Python 1.0.0 Released

## Overview

We are excited to announce the public preview release of [MSAL Python v1.0.0](https://github.com/AzureAD/microsoft-authentication-library-for-python/releases/tag/1.0.0). MSAL Python is the recommended authentication library for Python applications to implement client side authentication flows using the [Microsoft identity platform](https://aka.ms/aaddevv2). It allows you to sign in users or apps with Microsoft identities (Azure AD, Microsoft accounts and Azure AD B2C accounts) and obtain tokens to call Microsoft APIs such as [Microsoft Graph](https://graph.microsoft.io/) or your own APIs registered with the Microsoft identity platform.

With the 1.0.0 release, MSAL Python achieves feature parity with the previous [ADAL Python](https://github.com/AzureAD/azure-activedirectory-library-for-python) library for Azure AD authentication scenarios. Additionally, MSAL Python allows your application to integrate with [Azure AD B2C](https://docs.microsoft.com/en-us/azure/active-directory-b2c/active-directory-b2c-overview#identity-providers).
The 1.0.0 version also marks the release of a production supported library with a stable API surface. We encourage you to try out [the latest MSAL Python package](https://pypi.org/project/msal/) and [update your existing applications](https://docs.microsoft.com/en-us/azure/active-directory/develop/migrate-python-adal-msal) to use MSAL Python.

## Key highlights

Here are the great features you get with **MSAL Python 1.0.0**:

- A production supported library. MSAL Python is in public preview; however, the library is now stable and production ready. We will soon be making a GA release.
- An updated API that has conceptual consistency with the other MSAL SDKs. The API in v1.0.0 is stable and any future breaking changes will only be made in a Major version following [Semantic Versioning](https://semver.org/).
- Integration with the [Microsoft identity platform](https://aka.ms/aaddevv2) allows authentication with Azure AD, MSA and Azure AD B2C accounts. You can find the list of [supported application types and scenarios here](https://docs.microsoft.com/en-us/azure/active-directory/develop/authentication-flows-app-scenarios#scenarios-and-supported-platforms-and-languages).
- Feature parity with ADAL Python for Azure AD scenarios.  Refer to this [migration guide](https://docs.microsoft.com/en-us/azure/active-directory/develop/migrate-python-adal-msal) to update your applications from ADAL to MSAL.
- Support for direct integration with [ADFS 2019](https://docs.microsoft.com/en-us/azure/active-directory/develop/msal-python-adfs-support).
- Support for sharing the [token cache](https://docs.microsoft.com/en-us/azure/active-directory/develop/msal-python-token-cache-serialization) with applications using other MSALs such as MSAL Java and MSAL .NET.
- [Developer samples](https://github.com/AzureAD/microsoft-authentication-library-for-python/tree/dev/sample) for different scenarios supported by MSAL Python.  

You can find more details in the [Release notes](https://github.com/AzureAD/microsoft-authentication-library-for-python/releases).

## Get started

You can get started with MSAL Python by following this [quickstart sample for a web app](https://docs.microsoft.com/en-us/azure/active-directory/develop/quickstart-v2-python-webapp).
To learn more visit the [MSAL Python wiki](https://github.com/AzureAD/microsoft-authentication-library-for-python/wiki).
