# @ohos.identifier.oaid (OAID)

<!--Kit: Ads Kit-->
<!--Subsystem: Advertising-->
<!--Owner: @SukiEvas-->
<!--Designer: @zhansf1988-->
<!--Tester: @hongmei_may-->
<!--Adviser: @RayShih-->
<!-- md-trans-meta sourceCommit=ea2d8082679fb01eb444ae8d25a7681c82490ad7 translatedAt=2026-05-25T06:56:55.074Z pushedAt=2026-05-27T13:10:05.576Z -->

This module provides the capability of obtaining and resetting the Open Anonymous Device Identifier (OAID).

> **NOTE**<br>
> <br>
> The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.<br>
> <br>
> To use the API for obtaining the OAID, you need to [request user authorization](../../security/AccessToken/request-user-authorization.md) (the permission is enabled by default): ohos.permission.APP_TRACKING_CONSENT.

## Modules to Import

```typescript
import { identifier } from '@kit.AdsKit';
```

## identifier.getOAID

getOAID(): Promise&lt;string&gt;

Obtains the OAID. This API uses a promise to return the result.

**Required permissions**: ohos.permission.APP_TRACKING_CONSENT

**System capability**: SystemCapability.Advertising.OAID

**Return value**

| Type | Description | 
|-----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Promise&lt;string&gt; | Promise used to return the OAID.<br/>1. If the app has configured the ohos.permission.APP_TRACKING_CONSENT permission and the cross-app association access permission is allowed, the OAID is returned.<br/>2. If the app has configured the ohos.permission.APP_TRACKING_CONSENT permission and the cross-app association access permission is disallowed, 00000000-0000-0000-0000-000000000000 is returned.<br/>3. If the app has not configured the ohos.permission.APP_TRACKING_CONSENT permission, 00000000-0000-0000-0000-000000000000 is returned. |

**Error codes**

For details about the error codes, see [OAID Error Codes](errorcode-oaid.md).

| ID| Error Message                        |
|----------|----------------------------------|
| 17300001 | System&nbsp;internal&nbsp;error. |

**Example**

```ts
import { identifier } from '@kit.AdsKit';

identifier.getOAID().then((data: string) => {
  const oaid: string = data;
});
```

## identifier.getOAID

getOAID(callback: AsyncCallback&lt;string&gt;): void

Obtains the OAID. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.APP_TRACKING_CONSENT

**System capability**: SystemCapability.Advertising.OAID

**Parameters**

| Parameter Name | Type | Mandatory | Description | 
| -------- | -------- | -------- | -------- |
| callback | AsyncCallback&lt;string&gt; | Yes | Callback used to return the OAID.<br/>1. If the app has configured the ohos.permission.APP_TRACKING_CONSENT permission and the cross-app association access permission is allowed, the OAID is returned.<br/>2. If the app has configured the ohos.permission.APP_TRACKING_CONSENT permission and the cross-app association access permission is disallowed, 00000000-0000-0000-0000-000000000000 is returned.<br/>3. If the app has not configured the ohos.permission.APP_TRACKING_CONSENT permission, 00000000-0000-0000-0000-000000000000 is returned. |

> **NOTE**<br>
> <br>
> The setting item of cross-app association access permission was named app tracking access permission in HarmonyOS NEXT Developer Beta5 and earlier versions.

**Error codes**

For details about the error codes, see [OAID Error Codes](errorcode-oaid.md).

| ID| Error Message                        |
|----------|----------------------------------|
| 17300001 | System internal error. |

**Example**

```typescript
import { identifier } from '@kit.AdsKit';
import { BusinessError } from '@kit.BasicServicesKit';

identifier.getOAID((err: BusinessError, data: string) => {
  if (err.code) {
    return;
  }
  const oaid: string = data;
});
```