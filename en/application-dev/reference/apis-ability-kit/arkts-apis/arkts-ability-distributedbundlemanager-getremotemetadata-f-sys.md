# getRemoteMetadata (System API)

## Modules to Import

```TypeScript
import { distributedBundleManager } from '@kit.AbilityKit';
```

## getRemoteMetadata

```TypeScript
function getRemoteMetadata(deviceId: string, bundleName: string): Promise<Array<ModuleMetadata>>
```

Obtains the metadata of an app with a specified bundle name on a specified remote device. This API uses a promise to return the result.

**Since:** 26.1.0

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BundleManager.DistributedBundleFramework

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceId | string | Yes | ID of the remote device, which is actually the networkId (distributed network identifier). You can call getAvailableDeviceList to obtain all trusted device lists; the value is the networkId field in the trusted device information. |
| bundleName | string | Yes | Bundle name of the app. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[ModuleMetadata](arkts-ability-applicationinfo-modulemetadata-i.md)&gt;&gt; | Promise used to return an array of ModuleMetadata. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundle name is not found. |
| [17700007](../errorcode-bundle.md#17700007-incorrect-device-id) | The specified device ID is not found. |
| [17700027](../errorcode-bundle.md#17700027-distributed-service-is-not-started) | The distributed service is not running. |
