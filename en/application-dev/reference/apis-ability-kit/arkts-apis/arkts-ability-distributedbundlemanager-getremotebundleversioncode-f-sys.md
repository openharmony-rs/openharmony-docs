# getRemoteBundleVersionCode (System API)

## Modules to Import

```TypeScript
import { distributedBundleManager } from '@kit.AbilityKit';
```

## getRemoteBundleVersionCode

```TypeScript
function getRemoteBundleVersionCode(deviceId: string, bundleName: string): Promise<number>
```

Obtains the version code of the application with the specified bundle name on the specified remote device. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**Model restriction:** This API can be used only in the stage model.

<!--Device-distributedBundleManager-function getRemoteBundleVersionCode(deviceId: string, bundleName: string): Promise<long>--><!--Device-distributedBundleManager-function getRemoteBundleVersionCode(deviceId: string, bundleName: string): Promise<long>-End-->

**System capability:** SystemCapability.BundleManager.DistributedBundleFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceId | string | Yes | ID of the remote device. You can call [getAvailableDeviceList](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#getavailabledevicelist) to obtain all trusted device lists. The value is the **networkId** field in the trusted device information. |
| bundleName | string | Yes | Bundle name of the app. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the result. The version code is returned if the call succeeds; an error object is returned if the call fails. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundle name is not found. |
| [17700007](../errorcode-bundle.md#17700007-incorrect-device-id) | The specified device ID is not found. |
| [17700027](../errorcode-bundle.md#17700027-distributed-service-is-not-started) | The distributed service is not running. |

<!--Del-->
**Examples**

```TypeScript
import { distributedBundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  distributedBundleManager.getRemoteBundleVersionCode('1111', 'com.hap.myapplication').then((data: number) => {
    console.info(`getRemoteBundleVersionCode succeed:` + data);
  }).catch((err: BusinessError) => {
    console.error(`getRemoteBundleVersionCode failed: error code is ${err.code}  and error msg is ${err.message}`);
  });
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error(`getRemoteBundleVersionCode failed: error code is ${code}  and error msg is ${message}`);
}
```

<!--DelEnd-->
