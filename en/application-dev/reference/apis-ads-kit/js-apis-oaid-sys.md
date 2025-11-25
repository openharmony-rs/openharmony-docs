# @ohos.identifier.oaid (OAID) (System API)

<!--Kit: Ads Kit-->
<!--Subsystem: Advertising-->
<!--Owner: @SukiEvas-->
<!--Designer: @zhansf1988-->
<!--Tester: @hongmei_may-->
<!--Adviser: @RayShih-->

This module provides the capability of resetting open anonymous device identifiers (OAIDs).

> **NOTE**<br>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.<br>
> - To use the OAID APIs, you must [request authorization from users](../../security/AccessToken/request-user-authorization.md): ohos .permission.APP_TRACKING_CONSENT.<br>
> - This topic describes only the system APIs provided by the module. For details about its public APIs, see [@ohos.identifier.oaid (OAID)](js-apis-oaid.md).

## Modules to Import

```ts
import { identifier } from '@kit.AdsKit';
```

## identifier.resetOAID

resetOAID(): void

Resets the OAID.

**System API**: This is a system API.

**System capability**: SystemCapability.Advertising.OAID

**Error codes**

For details about the error codes, see [OAID Error Codes](errorcode-oaid.md).

| ID| Error Message                                                                    |
|----------|------------------------------------------------------------------------------|
| 202      | Permission verification failed. A non-system application calls a system API. |
| 17300001 | System internal error.                                                       |
| 17300002 | Not in the trust list.                                                       |

**Example**

```ts
import { identifier } from '@kit.AdsKit';

identifier.resetOAID();
```
