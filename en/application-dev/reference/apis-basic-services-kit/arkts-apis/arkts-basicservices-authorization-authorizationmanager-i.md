# AuthorizationManager

Defines the authorization manager, which is used to request and check the authorization.

**Since:** 26.1.0

**System capability:** SystemCapability.Account.OsAccount

## Modules to Import

```TypeScript
import { authorization } from '@kit.BasicServicesKit';
```

## hasAuthorization

```TypeScript
hasAuthorization(privilege: Privilege): Promise<boolean>
```

Checks whether the current process has authorization for the specified privilege. This API uses a promise to return the result.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| privilege | [Privilege](arkts-basicservices-authorization-privilege-e.md) | Yes | Target privilege. For available values, see [Privilege](arkts-basicservices-authorization-privilege-e.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result. The value **true** indicates that the current process has authorization for the specified privilege; **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |

## requestAuthorization

```TypeScript
requestAuthorization(privilege: Privilege, context: UIAbilityContext): Promise<AuthorizationResult>
```

Requests that the specified privilege be granted to the current process. This API uses a promise to return the result.

When the application is in the foreground and there is no valid authorization, the authorization dialog is displayed in modal application mode. If a valid authorization already exists, it will be reused.

**Since:** 26.1.0

**Required permissions:** ohos.permission.REQUEST_LOCAL_ACCOUNT_AUTHORIZATION

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Account.OsAccount

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| privilege | [Privilege](arkts-basicservices-authorization-privilege-e.md) | Yes | Target privilege. For available values, see [Privilege](arkts-basicservices-authorization-privilege-e.md). |
| context | [UIAbilityContext](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext-c.md) | Yes | The [UIAbility context](../../apis-ability-kit/arkts-apis/arkts-ability-uiabilitycontext-c.md) that hosts the authorization dialog. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AuthorizationResult](arkts-basicservices-authorization-authorizationresult-i.md)&gt; | Promise used to return the authorization result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [12300001](../errorcode-account.md#12300001-system-service-abnormal) | The system service works abnormally. |
| 12300302 | User interaction is required but not allowed. Possible causes: 1. The specified UI context is invalid; 2. The application is not in the foreground. Suggested solutions: Ensure the application is in the foreground and pass a valid UIAbilityContext. |
| 12300304 | Authorization service is busy. Possible cause: Another authorization is being processed. |
