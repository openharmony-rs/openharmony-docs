# @ohos.account.appAccount(Application Account Management)

The **appAccount** module provides APIs for adding, deleting, modifying, and querying application account information. The application-level account isolation mechanism is used for application account management. The account information of each application is managed separately.

**Since:** 7

**System capability:** SystemCapability.Account.AppAccount

## Modules to Import

```TypeScript
import { appAccount } from '@kit.BasicServicesKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [createAppAccountManager](arkts-basicservices-appaccount-createappaccountmanager-f.md) | Creates an **AppAccountManager** object. |

### Classes

| Name | Description |
| --- | --- |
| [Authenticator](arkts-basicservices-appaccount-authenticator-c.md) | Defines an authenticator. |

### Interfaces

| Name | Description |
| --- | --- |
| [AppAccountInfo](arkts-basicservices-appaccount-appaccountinfo-i.md) | Defines application account information. |
| [AppAccountManager](arkts-basicservices-appaccount-appaccountmanager-i.md) | Defines the application account manager, which is used to manage account information of applications. |
| [AuthCallback](arkts-basicservices-appaccount-authcallback-i.md) | Defines authenticator callbacks. |
| [AuthenticatorCallback](arkts-basicservices-appaccount-authenticatorcallback-i.md) | Provides OAuth authenticator callbacks. |
| [AuthenticatorInfo](arkts-basicservices-appaccount-authenticatorinfo-i.md) | Defines OAuth authenticator information. |
| [AuthResult](arkts-basicservices-appaccount-authresult-i.md) | Defines the authentication result. |
| [AuthTokenInfo](arkts-basicservices-appaccount-authtokeninfo-i.md) | Defines authorization token information. |
| [CreateAccountImplicitlyOptions](arkts-basicservices-appaccount-createaccountimplicitlyoptions-i.md) | Defines the options for implicitly creating an application account. |
| [CreateAccountOptions](arkts-basicservices-appaccount-createaccountoptions-i.md) | Defines the options for creating an application account. |
| [OAuthTokenInfo](arkts-basicservices-appaccount-oauthtokeninfo-i.md) | Defines authorization token information. |
| [SelectAccountsOptions](arkts-basicservices-appaccount-selectaccountsoptions-i.md) | Defines the options for selecting accounts. |
| [SetPropertiesOptions](arkts-basicservices-appaccount-setpropertiesoptions-i.md) | Represents the options for setting authenticator properties. |
| [VerifyCredentialOptions](arkts-basicservices-appaccount-verifycredentialoptions-i.md) | Represents the options for verifying the user credential. |

### Enums

| Name | Description |
| --- | --- |
| [Constants](arkts-basicservices-appaccount-constants-e.md) | Enumerates the constants. |
| [ResultCode](arkts-basicservices-appaccount-resultcode-e.md) | Enumerates the result codes. |
