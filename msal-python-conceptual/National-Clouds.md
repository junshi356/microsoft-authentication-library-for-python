National clouds (aka Sovereign clouds) are physically isolated instances of Azure. These regions of Azure are designed to make sure that data residency, sovereignty, and compliance requirements are honored within geographical boundaries.

In addition to the public cloud​, Azure Active Directory is deployed in the following National clouds:  

- Azure US Government
- Azure China 21Vianet
- Azure Germany

Note that enabling your application for national clouds requires you to:

- Register your application in a specific portal, depending on the cloud. For more information on how to choose the portal refer [App registration endpoints](https://docs.microsoft.com/en-us/azure/active-directory/develop/authentication-national-cloud#app-registration-endpoints)
- Use any of the [samples](https://github.com/AzureAD/microsoft-authentication-library-for-python/tree/dev/sample) from the repo with a few changes to the configuration, depending on the cloud, which are mentioned next.
- Use a specific authority, depending on the cloud you registered the application in. For more information on authorities for different clouds, refer [Azure AD Authentication endpoints](https://docs.microsoft.com/en-us/azure/active-directory/develop/authentication-national-cloud#azure-ad-authentication-endpoints).
An example authority:
```json
"authority": "https://login.microsoftonline.us/Enter_the_Tenant_Info_Here"
```

- In case you want to call the graph, this requires a specific Graph endpoint URL, depending on the cloud. To find Microsoft Graph endpoints for all the national clouds, refer [Microsoft Graph and Graph Explorer service root endpoints](https://docs.microsoft.com/en-us/graph/deployments#microsoft-graph-and-graph-explorer-service-root-endpoints
). An example of a graph endpoint with scope is:

```json
"endpoint" : "https://graph.microsoft.us/v1.0/me"
"scope": "User.Read"
```
