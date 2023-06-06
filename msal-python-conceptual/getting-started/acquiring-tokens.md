---
title: Acquiring tokens
description: "There are many ways of acquiring a token. Some require user interaction through a web browser. Some don't require any user interaction."
---

# Acquiring tokens

As explained in [scenarios](./scenarios.md), there are many ways of acquiring a token. Some require user interaction through a web browser. Some don't require any user interaction.
In general the way to acquire a token is different depending on the application type-  public client application (Desktop / Mobile) or a confidential client application (Web App, Web API, daemon application like a windows service)

## Prerequisites

Before acquiring tokens with MSAL Python:

- Instantiate a [client application](./client-applications.md)

## Token acquisition methods

Follow the topics below for detailed explanation with MSAL Python code usage for each token acquisition method.

### Public client applications

- Acquire tokens by [authorization code](/azure/active-directory/develop/scenario-desktop-acquire-token?tabs=python#acquiring-a-token-interactively) after letting the user sign-in through the authorization request URL.
- It's also possible (but not recommended) to get a token with a [username and password](/azure/active-directory/develop/scenario-desktop-acquire-token?tabs=python#username--password).
- Finally, for applications running on devices which don't have a web browser, it's possible to acquire a token through the [device code flow](/azure/active-directory/develop/scenario-desktop-acquire-token?tabs=python#command-line-tool-without-web-browser), which provides the user with a URL and a code. The user goes to a web browser on another device, enters the code and signs-in, and then Azure AD returns back a token to the browser-less device.

### Confidential client applications

- Acquire token **as the application itself** using [client credentials](/azure/active-directory/develop/scenario-daemon-acquire-token?tabs=python#acquiretokenforclient-api), and not for a user. For example, in apps which process users in batches and not a particular user such as in syncing tools.
- In the case of Web Apps or Web APIs **calling another downstream Web API in the name of the user**, use the [On Behalf Of flow](/azure/active-directory/develop/v2-oauth2-on-behalf-of-flow) to acquire a token based on some User assertion (SAML for instance, or a JWT token).
- **For Web apps in the name of a user**, acquire tokens by [authorization code](/azure/active-directory/develop/scenario-web-app-call-api-acquire-token?tabs=python) after letting the user sign-in through the authorization request URL. This is typically the mechanism used by an application which lets the user sign-in using Open ID Connect, but then wants to access Web APIs for this particular user.

## MSAL Python caches tokens

For both Public client and Confidential client applications, MSAL maintains a token cache, and applications should try to get a token from the cache first before any other means. Take a look at the [recommended pattern](/azure/active-directory/develop/scenario-desktop-acquire-token?tabs=python) for token acquisition.

To be able to make use of the cache, the application needs to customize the [token cache serialization](/azure/active-directory/develop/msal-python-token-cache-serialization).
