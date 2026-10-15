# off (System API)

## Modules to Import

```TypeScript
import { bundleMonitor } from '@kit.AbilityKit';
```

## off

```TypeScript
function off(type: BundleChangedEvent, callback?: Callback<BundleChangedInfo>): void
```

Unsubscribes from bundle installation, uninstall, and update events. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.LISTEN_BUNDLE_CHANGE

<!--Device-bundleMonitor-function off(type: BundleChangedEvent, callback?: Callback<BundleChangedInfo>): void--><!--Device-bundleMonitor-function off(type: BundleChangedEvent, callback?: Callback<BundleChangedInfo>): void-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [BundleChangedEvent](arkts-ability-bundlemonitor-bundlechangedevent-t-sys.md) | Yes | Type of the event to unsubscribe from. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[BundleChangedInfo](arkts-ability-bundlemonitor-bundlechangedinfo-i-sys.md)&gt; | No | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md) used to return the result. If the operation is successful, err is undefined and data is the app change information obtained. Otherwise, err is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Verify permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

<!--Del-->
**Examples**

```TypeScript
import { bundleMonitor } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// The variable in this API must be the same as that in bundleMonitor.on. Otherwise, the callback cannot be unsubscribed from.
let callbackFun = (bundleChangeInfo: bundleMonitor.BundleChangedInfo) => {
  console.info(`bundleName : ${bundleChangeInfo.bundleName} userId : ${bundleChangeInfo.userId}`);
};

try {
  bundleMonitor.off('add', callbackFun);
} catch (errData) {
  let message = (errData as BusinessError).message;
  let errCode = (errData as BusinessError).code;
  console.error(`errData is errCode:${errCode}  message:${message}`);
}
```

<!--DelEnd-->
