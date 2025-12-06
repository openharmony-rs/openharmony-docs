# @ohos.identifier.oaid (OAID)

<!--Kit: Ads Kit-->
<!--Subsystem: Advertising-->
<!--Owner: @SukiEvas-->
<!--Designer: @zhansf1988-->
<!--Tester: @hongmei_may-->
<!--Adviser: @RayShih-->

This module provides the capability of obtaining open anonymous device identifiers (OAIDs).

> **NOTE**<br>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.<br>
> - To use the OAID APIs, you must [request authorization from users](../../security/AccessToken/request-user-authorization.md): ohos .permission.APP_TRACKING_CONSENT.

## Modules to Import

```ts
import { identifier } from '@kit.AdsKit';
```

## identifier.getOAID

getOAID(): Promise&lt;string&gt;

Obtains the OAID. This API uses a promise to return the result.

**Required permissions**: ohos.permission.APP_TRACKING_CONSENT

**System capability**: SystemCapability.Advertising.OAID

**Return value**

| Type                 | Description                                                                                                                                                                                                                                                                                                                                                                                                |
|-----------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Promise&lt;string&gt; | Promise used to return the OAID.<br>1. If the application has configured the permission **ohos.permission.APP_TRACKING_CONSENT** and the permission is allowed, the OAID is returned.<br>2. If the application has configured the permission **ohos.permission.APP_TRACKING_CONSENT** and the permission is disallowed, 00000000-0000-0000-0000-000000000000 is returned.<br>3. If the application has not configured the permission **ohos.permission.APP_TRACKING_CONSENT**, 00000000-0000-0000-0000-000000000000 is returned.|

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

| Name  | Type                       | Mandatory| Description                                                                                                                                                                                                                                                                                                                                                                                             |
|----------|-----------------------------|------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| callback | AsyncCallback&lt;string&gt; | Yes  | Callback used to return the OAID.<br>1. If the application has configured the permission **ohos.permission.APP_TRACKING_CONSENT** and the permission is allowed, the OAID is returned.<br>2. If the application has configured the permission **ohos.permission.APP_TRACKING_CONSENT** and the permission is disallowed, 00000000-0000-0000-0000-000000000000 is returned.<br>3. If the application has not configured the permission **ohos.permission.APP_TRACKING_CONSENT**, 00000000-0000-0000-0000-000000000000 is returned.|

**Error codes**

For details about the error codes, see [OAID Error Codes](errorcode-oaid.md).

| ID| Error Message                        |
|----------|----------------------------------|
| 17300001 | System&nbsp;internal&nbsp;error. |

**Example**

```ts
import { identifier } from '@kit.AdsKit';
import { BusinessError } from '@kit.BasicServicesKit';

identifier.getOAID((err: BusinessError, data: string) => {
  if (err.code) {
    return;
  }
  const oaid: string = data;
});
```
