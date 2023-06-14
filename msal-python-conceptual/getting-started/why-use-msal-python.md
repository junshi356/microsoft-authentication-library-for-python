---
title: Why use MSAL Python?
description: "MSAL Python (Microsoft Authentication Library for Python) enables developers to acquire tokens in order to call secured Web APIs**. These Web APIs can be the Microsoft Graph, other Microsoft APIS, 3rd party Web APIs, or your own Web API."
---

# Why use MSAL Python?

MSAL Python ([Microsoft Authentication Library for Python](https://github.com/AzureAD/microsoft-authentication-library-for-python)) enables developers to [acquire tokens](./acquiring-tokens.md) in order to call secured Web APIs. These Web APIs can be Microsoft Graph, other Microsoft APIS, 3rd party Web APIs, or your own Web API.

## MSAL Python Supports multiple application architectures

MSAL Python supports all the possible application topologies including:

- [native client](/azure/active-directory/develop/active-directory-dev-glossary#native-client)  (desktop applications) calling the Microsoft Graph in the name of the user,
- daemons/services or [web clients](/azure/active-directory/develop/active-directory-dev-glossary#web-client)  (Web Apps/ Web APIs) calling the Microsoft Graph in the name of a user, or without a user.

With the exception of:

- [User-agent based client](/azure/active-directory/develop/active-directory-dev-glossary#user-agent-based-client) which is only supported in JavaScript

For details about the supported scenarios see [Scenarios](https://github.com/AzureAD/microsoft-authentication-library-for-python/wiki/Scenarios).

## Added value by using MSAL Python over OAuth libraries or coding against the protocol

MSAL Python is a token acquisition library. Depending on your scenario it provides you with various way of getting a token, with a consistent API for a number of platforms.
It also adds value by:

- maintaining a **token cache** and **refreshes tokens** for you when they are close to expire.
  > you don't need to handle expiration on your own.
- helping you specify which **audience** you want your application to sign-in (your org, several orgs, work and school and Microsoft personal accounts, Social identities with Azure AD B2C, users in sovereign and national clouds)
- **helping you troubleshoot** your app by exposing actionable exceptions, logging and telemetry.

## MSAL Python is about acquiring tokens, not protecting an API

MSAL Python is used to acquire tokens. It's not used to protect a Web API. If you are interested in protecting a Web API with Azure AD, you might want to check out:

- [Validating tokens manually](/azure/active-directory/develop/access-tokens#validating-tokens)
