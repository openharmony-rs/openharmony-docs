# @ohos.account.osAccount.authorization

Provides OS local account authorization management capabilities. You can use the APIs in this namespace to request authorization for specified [Privileges](arkts-basicservices-authorization-privilege-e.md), which are granted based on authorization policies and user consent.

> **NOTE:** 
> Failures are reported through two channels. A thrown [BusinessError](arkts-basicservices-base-businesserror-i.md) means the request is
> not accepted at all (for example, 201 means the caller lacks the API-level permission
> ohos.permission.REQUEST_LOCAL_ACCOUNT_AUTHORIZATION; 12300302 means user interaction is required but not allowed).
> A [AuthorizationResultCode](arkts-basicservices-authorization-authorizationresultcode-e.md) in the resolved result means the request was accepted and reports
> the outcome:
> [AUTHORIZATION_CANCELED](arkts-basicservices-authorization-authorizationresultcode-e.md#authorization_canceled) means the user canceled the authorization request;
> [AUTHORIZATION_DENIED](arkts-basicservices-authorization-authorizationresultcode-e.md#authorization_denied) means the authorization policy is not met;
> [AUTHORIZATION_NOT_SUPPORTED](arkts-basicservices-authorization-authorizationresultcode-e.md#authorization_not_supported) means
> the configuration for the privilege is not deployed in the current system version.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Account.OsAccount

## Modules to Import

```TypeScript
import { authorization } from '@kit.BasicServicesKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getAuthorizationManager](arkts-basicservices-authorization-getauthorizationmanager-f.md) | Obtains an [AuthorizationManager](arkts-basicservices-authorization-authorizationmanager-i.md) instance. |

### Interfaces

| Name | Description |
| --- | --- |
| [AuthorizationManager](arkts-basicservices-authorization-authorizationmanager-i.md) | Defines the authorization manager, which is used to request and check the authorization. |
| [AuthorizationResult](arkts-basicservices-authorization-authorizationresult-i.md) | Defines the authorization result. Currently, the authorization validity period of all [Privileges](arkts-basicservices-authorization-privilege-e.md) follows the lifecycle of the caller process. |

### Enums

| Name | Description |
| --- | --- |
| [AuthorizationResultCode](arkts-basicservices-authorization-authorizationresultcode-e.md) | Enumerates authorization result codes. |
| [Privilege](arkts-basicservices-authorization-privilege-e.md) | Enumerates the privileges that can be authorized. Before requesting authorization for these privileges, ensure that the current application and runtime environment meet the authorization policy requirements. For detailed definitions of each privilege (including authorization policies), see [Privilege Appendix](../../../reference/apis-basic-services-kit/appendix-osAccount-authorization-privileges.md). |
