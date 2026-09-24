# getOAID

## Modules to Import

```TypeScript
import { identifier } from '@kit.AdsKit';
```

## getOAID

```TypeScript
function getOAID(callback: AsyncCallback<string>): void
```

Obtains the OAID. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> The setting item of cross-app association access permission was named app tracking access permission
> in HarmonyOS NEXT Developer Beta5 and earlier versions.

**Since:** 10

**Required permissions:** ohos.permission.APP_TRACKING_CONSENT

**System capability:** SystemCapability.Advertising.OAID

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Callback used to return the OAID. 1. If the app has configured the ohos.permission.APP_TRACKING_CONSENT permission and the cross-app association access permission is allowed, the OAID is returned. 2. If the app has configured the ohos.permission.APP_TRACKING_CONSENT permission and the cross-app association access permission is disallowed, 00000000-0000-0000-0000-000000000000 is returned. 3. If the app has not configured the ohos.permission.APP_TRACKING_CONSENT permission, 00000000-0000-0000-0000-000000000000 is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17300001](../errorcode-oaid.md#17300001-system-internal-error) | System internal error. |

**Examples**

```TypeScript
import { identifier } from '@kit.AdsKit';
import { BusinessError } from '@kit.BasicServicesKit';

identifier.getOAID((err: BusinessError, data: string) => {
  if (err.code) {
    return;
  }
  const oaid: string = data;
});
```


<a id="getoaid-1"></a>

## getOAID

```TypeScript
function getOAID(): Promise<string>
```

Obtains the OAID. This API uses a promise to return the result.

> **NOTE:** 
> 
> The setting item of cross-app association access permission was named app tracking access permission
> in HarmonyOS NEXT Developer Beta5 and earlier versions.

**Since:** 10

**Required permissions:** ohos.permission.APP_TRACKING_CONSENT

**System capability:** SystemCapability.Advertising.OAID

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the OAID. 1. If the app has configured the ohos.permission.APP_TRACKING_CONSENT permission and the cross-app association access permission is allowed, the OAID is returned. 2. If the app has configured the ohos.permission.APP_TRACKING_CONSENT permission and the cross-app association access permission is disallowed, 00000000-0000-0000-0000-000000000000 is returned. 3. If the app has not configured the ohos.permission.APP_TRACKING_CONSENT permission, 00000000-0000-0000-0000-000000000000 is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [17300001](../errorcode-oaid.md#17300001-system-internal-error) | System internal error. |

**Examples**

```TypeScript
import { identifier } from '@kit.AdsKit';

identifier.getOAID().then((data: string) => {
  const oaid: string = data;
});
```
