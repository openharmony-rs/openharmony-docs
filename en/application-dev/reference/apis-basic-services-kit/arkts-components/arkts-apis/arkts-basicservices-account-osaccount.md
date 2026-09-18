# @ohos.account.osAccount

The **osAccount** module provides basic capabilities for managing system (OS) accounts, including adding, deleting, querying, setting, subscribing to, and enabling an OS account.

**Since:** 7

**System capability:** SystemCapability.Account.OsAccount

## Modules to Import

```TypeScript
import { osAccount } from '@kit.BasicServicesKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getAccountManager](arkts-basicservices-osaccount-getaccountmanager-f.md) | Obtains an **AccountManager** instance. |
| [isDomainAccountSupported](arkts-basicservices-osaccount-isdomainaccountsupported-f.md) | Checks whether this domain account is supported. This API uses a promise to return the result. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getAuthorizationManager](arkts-basicservices-osaccount-getauthorizationmanager-f-sys.md) | Obtains the current OS account authorization manager. |
| [getOsAccountSubProfileManager](arkts-basicservices-osaccount-getosaccountsubprofilemanager-f-sys.md) | Obtains the OS account sub-profile manager. |
<!--DelEnd-->

### Classes

| Name | Description |
| --- | --- |
| [DomainAccountManager](arkts-basicservices-osaccount-domainaccountmanager-c.md) | Provides APIs for domain account management. |
| [DomainServerConfigManager](arkts-basicservices-osaccount-domainserverconfigmanager-c.md) | Provides APIs for domain server configuration and management. |

<!--Del-->
### Classes(System API)

| Name | Description |
| --- | --- |
| [DomainAccountManager](arkts-basicservices-osaccount-domainaccountmanager-c-sys.md) | Provides APIs for domain account management. |
| [InputerManager](arkts-basicservices-osaccount-inputermanager-c-sys.md) | Provides APIs for managing credential inputers. |
| [PINAuth](arkts-basicservices-osaccount-pinauth-c-sys.md) | Provides APIs for PIN authentication. |
| [UserAuth](arkts-basicservices-osaccount-userauth-c-sys.md) | Provides APIs for user authentication. |
| [UserIdentityManager](arkts-basicservices-osaccount-useridentitymanager-c-sys.md) | Provides APIs for managing the user identity. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [AccountManager](arkts-basicservices-osaccount-accountmanager-i.md) | Provides APIs for managing OS accounts. |
| [DomainAccountInfo](arkts-basicservices-osaccount-domainaccountinfo-i.md) | Represents domain account information. |
| [DomainServerConfig](arkts-basicservices-osaccount-domainserverconfig-i.md) | Represents the configuration of a domain server. |
| [OsAccountInfo](arkts-basicservices-osaccount-osaccountinfo-i.md) | Represents the OS account information. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [AccountManager](arkts-basicservices-osaccount-accountmanager-i-sys.md) | Provides APIs for managing OS accounts. |
| [AcquireAuthorizationOptions](arkts-basicservices-osaccount-acquireauthorizationoptions-i-sys.md) | Defines the options for acquiring the authorization. |
| [AcquireAuthorizationResult](arkts-basicservices-osaccount-acquireauthorizationresult-i-sys.md) | Defines the result of the authorization. |
| [AuthOptions](arkts-basicservices-osaccount-authoptions-i-sys.md) | Represents a set of optional parameters for [auth](arkts-basicservices-osaccount-userauth-c-sys.md#auth). |
| [AuthorizationManager](arkts-basicservices-osaccount-authorizationmanager-i-sys.md) | Defines the OS account authorization manager class. |
| [AuthResult](arkts-basicservices-osaccount-authresult-i-sys.md) | Defines the authentication result information. |
| [AuthStatusInfo](arkts-basicservices-osaccount-authstatusinfo-i-sys.md) | Presents the authentication status information. |
| [ConstraintChangeInfo](arkts-basicservices-osaccount-constraintchangeinfo-i-sys.md) | Defines the constraint change information. |
| [ConstraintSourceTypeInfo](arkts-basicservices-osaccount-constraintsourcetypeinfo-i-sys.md) | Defines the constraint source type. |
| [CreateOsAccountForDomainOptions](arkts-basicservices-osaccount-createosaccountfordomainoptions-i-sys.md) | Represents a set of optional parameters for creating an OS account bound to the specified domain account. It inherits from [CreateOsAccountOptions](arkts-basicservices-osaccount-createosaccountoptions-i-sys.md). |
| [CreateOsAccountOptions](arkts-basicservices-osaccount-createosaccountoptions-i-sys.md) | Represents the optional parameter used to create an OS account. |
| [CredentialChangeInfo](arkts-basicservices-osaccount-credentialchangeinfo-i-sys.md) | Defines the credential change information. |
| [CredentialInfo](arkts-basicservices-osaccount-credentialinfo-i-sys.md) | Defines the credential information. |
| [DomainAccountAuthOptions](arkts-basicservices-osaccount-domainaccountauthoptions-i-sys.md) | Defines the options for domain account authentication. |
| [DomainAccountInfo](arkts-basicservices-osaccount-domainaccountinfo-i-sys.md) | Represents domain account information. |
| [DomainPlugin](arkts-basicservices-osaccount-domainplugin-i-sys.md) | Provides APIs for domain account authentication. |
| [EnrolledCredInfo](arkts-basicservices-osaccount-enrolledcredinfo-i-sys.md) | Defines enrolled credential information. |
| [ExecutorProperty](arkts-basicservices-osaccount-executorproperty-i-sys.md) | Defines the executor property. |
| [GetAuthInfoOptions](arkts-basicservices-osaccount-getauthinfooptions-i-sys.md) | Represents a set of optional parameters for [GetAuthInfo](arkts-basicservices-osaccount-useridentitymanager-c-sys.md#getauthinfo). |
| [GetDomainAccessTokenOptions](arkts-basicservices-osaccount-getdomainaccesstokenoptions-i-sys.md) | Defines the options for obtaining a domain access token. |
| [GetDomainAccountInfoOptions](arkts-basicservices-osaccount-getdomainaccountinfooptions-i-sys.md) | Defines the options for obtaining domain account information. |
| [GetDomainAccountInfoPluginOptions](arkts-basicservices-osaccount-getdomainaccountinfopluginoptions-i-sys.md) | Defines the options for the domain plug-in to obtain the domain account information. The **GetDomainAccountInfoPluginOptions** class inherits from [**GetDomainAccountInfoOptions**](arkts-basicservices-osaccount-getdomainaccountinfooptions-i-sys.md). |
| [GetInputDataOptions](arkts-basicservices-osaccount-getinputdataoptions-i-sys.md) | Represents a set of optional parameters for [onGetData](arkts-basicservices-osaccount-iinputer-i-sys.md#ongetdata). |
| [GetPropertyRequest](arkts-basicservices-osaccount-getpropertyrequest-i-sys.md) | Defines the request for obtaining property information. |
| [IIdmCallback](arkts-basicservices-osaccount-iidmcallback-i-sys.md) | Provides callbacks for IDM. |
| [IInputData](arkts-basicservices-osaccount-iinputdata-i-sys.md) | Provides the password data callback. |
| [IInputer](arkts-basicservices-osaccount-iinputer-i-sys.md) | Provides callbacks to obtain credential inputer data. |
| [IUserAuthCallback](arkts-basicservices-osaccount-iuserauthcallback-i-sys.md) | Provides callbacks for user authentication. |
| [OsAccountInfo](arkts-basicservices-osaccount-osaccountinfo-i-sys.md) | Represents the OS account information. |
| [OsAccountSubProfile](arkts-basicservices-osaccount-osaccountsubprofile-i-sys.md) | Defines an OS account sub-profile. |
| [OsAccountSubProfileEventData](arkts-basicservices-osaccount-osaccountsubprofileeventdata-i-sys.md) | Defines the data of an OS account sub-profile event. |
| [OsAccountSubProfileManager](arkts-basicservices-osaccount-osaccountsubprofilemanager-i-sys.md) | Defines an OS account sub-profile manager. |
| [OsAccountSwitchEventData](arkts-basicservices-osaccount-osaccountswitcheventdata-i-sys.md) | Defines the event that indicates the start or end of a foreground-background OS account switchover. |
| [RemoteAuthOptions](arkts-basicservices-osaccount-remoteauthoptions-i-sys.md) | Represents a set of optional parameters for remote authentication. |
| [RemoveOsAccountOptions](arkts-basicservices-osaccount-removeosaccountoptions-i-sys.md) | Represents the optional parameter used to remove an OS account. |
| [RequestResult](arkts-basicservices-osaccount-requestresult-i-sys.md) | Defines the request result information. |
| [SetOsAccountTypeOptions](arkts-basicservices-osaccount-setosaccounttypeoptions-i-sys.md) | Defines the options for setting the OS account type. |
| [SetPropertyRequest](arkts-basicservices-osaccount-setpropertyrequest-i-sys.md) | Defines the request for setting property information. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [OsAccountType](arkts-basicservices-osaccount-osaccounttype-e.md) | Enumerates the OS account types. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [AuthIntent](arkts-basicservices-osaccount-authintent-e-sys.md) | Enumerates the authentication intents. |
| [AuthorizationResultCode](arkts-basicservices-osaccount-authorizationresultcode-e-sys.md) | Enumerates authorization result codes. |
| [AuthSubType](arkts-basicservices-osaccount-authsubtype-e-sys.md) | Enumerates the authentication credential subtypes. |
| [AuthTrustLevel](arkts-basicservices-osaccount-authtrustlevel-e-sys.md) | Enumerates the trust levels of the authentication result. |
| [AuthType](arkts-basicservices-osaccount-authtype-e-sys.md) | Enumerates the authentication credential types. |
| [ConstraintSourceType](arkts-basicservices-osaccount-constraintsourcetype-e-sys.md) | Enumerates the constraint sources. |
| [CredentialChangeType](arkts-basicservices-osaccount-credentialchangetype-e-sys.md) | Enumerates the credential change types. |
| [FaceTipsCode](arkts-basicservices-osaccount-facetipscode-e-sys.md) | Enumerates the tip codes for facial authentication. |
| [FingerprintTips](arkts-basicservices-osaccount-fingerprinttips-e-sys.md) | Enumerates the tip codes for fingerprint authentication. |
| [GetPropertyType](arkts-basicservices-osaccount-getpropertytype-e-sys.md) | Enumerates the types of properties to obtain. |
| [Module](arkts-basicservices-osaccount-module-e-sys.md) | Enumerates the modules from which information is obtained. |
| [OsAccountSubProfileEvent](arkts-basicservices-osaccount-osaccountsubprofileevent-e-sys.md) | Enumerates OS account sub-profile events. |
| [OsAccountType](arkts-basicservices-osaccount-osaccounttype-e-sys.md) | Enumerates the OS account types. |
| [ResultCode](arkts-basicservices-osaccount-resultcode-e-sys.md) | Enumerates the authentication result codes. |
| [SetPropertyType](arkts-basicservices-osaccount-setpropertytype-e-sys.md) | Enumerates the types of properties to set. |
<!--DelEnd-->
