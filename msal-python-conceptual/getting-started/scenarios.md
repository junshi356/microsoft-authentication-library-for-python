# Scenarios

MSAL Python can be used by applications to acquire tokens to access a protected API. Tokens can be acquired by different **application types**: Desktop applications, Web applications, Web APIs, and applications running on devices that don't have a browser (such as IoT). In MSAL Python, applications are categorized as follows:

- Public client applications (Desktop). These type of apps cannot store app secrets securely.
- Confidential client applications (Web apps, Web APIs, and daemon applications). These type of apps securely store a secret registered with Azure AD.

Learn more details about instantiating and configuring the above in [Client applications](Client-Applications) topic.
MSAL Python supports acquiring tokens either in the name of a user, or, in the name of the application itself (without a user). In the latter case, a confidential client application must be used.

MSAL Python can be used in applications running on different operating systems (Windows, Linux, Mac). Scenarios might differ depending on the platform.

Here are the key scenarios supported by MSAL Python. You can read the detailed explanations with MSAL Python code usage by following the links.

- [Web application that signs in users](/azure/active-directory/develop/scenario-web-app-sign-user-overview)
- [Web Application signing in a user and calling a Web API in the name of the user](/azure/active-directory/develop/scenario-web-app-call-api-overview) (Note: MSAL only helps the Web Application to sign in and obtain tokens. To [protect a web API](/azure/active-directory/develop/scenario-protected-web-api-overview), you will need other libraries.)
- [Desktop application calling a Web API in the name of the signed-in user](/azure/active-directory/develop/scenario-desktop-overview)
- [Desktop/service daemon application calling Web API without a user](/azure/active-directory/develop/scenario-daemon-overview)
- [Application without a browser, or IOT application calling an API in the name of the user](/azure/active-directory/develop/scenario-desktop-acquire-token?tabs=python#command-line-tool-without-web-browser)

Can't find the scenario you are looking for? Check out the [supported scenarios and platforms](/azure/active-directory/develop/authentication-flows-app-scenarios#scenarios-and-supported-platforms-and-languages) across MSALs.
