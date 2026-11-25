# @ohos.identifier.oaid (OAID) (System API)

<!--Kit: Ads Kit-->
<!--Subsystem: Advertising-->
<!--Owner: @ctssss-->
<!--Designer: @zhansf1988-->
<!--Tester: @hongmei_may-->
<!--Adviser: @RayShih-->
<!-- md-trans-meta sourceCommit=6493b14494a6c6b34e36a2da0a181b6e9e0f901d translatedAt=2026-11-23T09:12:29.670Z pushedAt=2026-11-24T11:55:17.141Z nl=1 -->

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