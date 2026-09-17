# setPowerConfig (System API)

## Modules to Import

```TypeScript
import { power } from '@kit.BasicServicesKit';
```

## setPowerConfig

```TypeScript
function setPowerConfig(sceneName: string, value: string): void
```

Update the power configuration value for a given scene name.

**Since:** 26.0.0

**Required permissions:** ohos.permission.POWER_CONFIG

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.PowerManager.PowerManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sceneName | string | Yes | Indicates the scene name of the power configuration. sceneName parameter must be a string and its length cannot exceed 128 bytes. |
| value | string | Yes | Indicates the power configuration value. value parameter must be a string and its length cannot exceed 128 bytes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [4900101](../errorcode-power.md#4900101-service-connection-failure) | Failed to connect to the service. |
| [4900400](../errorcode-power.md#4900400-incorrect-input-parameter) | Invalid parameter. Possible causes: 1. The sceneName or value parameter is an empty string; 2. The length of sceneName parameter exceeds 128 bytes; 3. The length of value parameter exceeds 128 bytes. |
| [4900601](../errorcode-power.md#4900601-failure-to-write-the-power-supply-configuration-node) | Failed to write the power configuration value. |

**Examples**

```TypeScript
try {
    power.setPowerConfig('scene_name_test', 'value_test');
    console.info('set power config success');
} catch(err) {
    console.error('set power config failed, err: ' + err);
}
```
