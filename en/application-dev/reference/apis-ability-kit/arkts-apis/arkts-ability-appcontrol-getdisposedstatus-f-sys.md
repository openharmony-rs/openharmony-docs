# getDisposedStatus (System API)

## Modules to Import

```TypeScript
import { appControl } from '@kit.AbilityKit';
```

## getDisposedStatus

```TypeScript
function getDisposedStatus(appId: string, callback: AsyncCallback<Want>): void
```

Obtains the disposed status of an application. This API uses an asynchronous callback to return the result. If the operation is successful, the disposed status of the application is returned. If the operation fails, an error message is returned.

**Since:** 9

**Required permissions:** ohos.permission.MANAGE_DISPOSED_APP_STATUS or ohos.permission.GET_DISPOSED_APP_STATUS

**System capability:** SystemCapability.BundleManager.BundleFramework.AppControl

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| appId | string | Yes | ID of the target application.<br> **appId** is the unique identifier of an application and is determined by the bundle name and signature information of the application. For details about how to obtain **appId**, see [How do I obtain appId from application information](../../../quick-start/common_problem_of_application.md#how-do-i-obtain-appid-from-application-information). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Want](arkts-ability-app-ability-want-want-c.md)&gt; | Yes | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md) used to return the result. If the operation is successful, **err** is **null** and **data** is the disposed status obtained; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [17700005](../errorcode-bundle.md#17700005-appid-is-an-empty-string) | The specified app ID is empty string. |

**Examples**

```TypeScript
import { appControl } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let appId = "com.example.myapplication_xxxxx";

try {
  appControl.getDisposedStatus(appId, (error, data) => {
    if (error) {
      let message = (error as BusinessError).message;
      console.error('getDisposedStatus failed ' + message);
      return;
    }
    console.info('getDisposedStatus success. DisposedStatus: ' + JSON.stringify(data));
  });
} catch (error) {
  let message = (error as BusinessError).message;
  console.error('getDisposedStatus failed ' + message);
}
```


<a id="getdisposedstatus-1"></a>

## getDisposedStatus

```TypeScript
function getDisposedStatus(appId: string): Promise<Want>
```

Obtains the disposed status of an application. This API uses a promise to return the result. If the operation is successful, the disposed status of the application is returned. If the operation fails, an error message is returned.

**Since:** 9

**Required permissions:** ohos.permission.MANAGE_DISPOSED_APP_STATUS or ohos.permission.GET_DISPOSED_APP_STATUS

**System capability:** SystemCapability.BundleManager.BundleFramework.AppControl

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| appId | string | Yes | ID of the target application.<br> **appId** is the unique identifier of an application and is determined by the bundle name and signature information of the application. For details about how to obtain **appId**, see [How do I obtain appId from application information](../../../quick-start/common_problem_of_application.md#how-do-i-obtain-appid-from-application-information). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Want](arkts-ability-app-ability-want-want-c.md)&gt; | Promise used to return the disposed status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [17700005](../errorcode-bundle.md#17700005-appid-is-an-empty-string) | The specified app ID is empty string. |

**Examples**

```TypeScript
import { appControl } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let appId = "com.example.myapplication_xxxxx";

try {
  appControl.getDisposedStatus(appId)
    .then((data) => {
      console.info('getDisposedStatus success. DisposedStatus: ' + JSON.stringify(data));
    }).catch((error: BusinessError) => {
    let message = (error as BusinessError).message;
    console.error('getDisposedStatus failed ' + message);
  });
} catch (error) {
  let message = (error as BusinessError).message;
  console.error('getDisposedStatus failed ' + message);
}
```
