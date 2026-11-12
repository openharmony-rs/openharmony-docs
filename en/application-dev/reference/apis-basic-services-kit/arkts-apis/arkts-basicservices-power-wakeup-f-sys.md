# wakeup (System API)

## Modules to Import

```TypeScript
import { power } from '@kit.BasicServicesKit';
```

## wakeup

```TypeScript
function wakeup(detail: string): void
```

Wakes up a device.

**Since:** 9

**Required permissions:** 
- API version 19 and later: ohos.permission.POWER_MANAGER
- API versions 9 to 18: N/A

<!--Device-power-function wakeup(detail: string): void--><!--Device-power-function wakeup(detail: string): void-End-->

**System capability:** SystemCapability.PowerManager.PowerManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| detail | string | Yes | Wakeup reason. The value must be a string. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; |
| [4900101](../errorcode-power.md#4900101-service-connection-failure) | Failed to connect to the service. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API.<br>**Applicable version:** 19 and later |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. This API cannot work in car devices.<br>**Applicable version:** 26.0.1 and later |

<!--Del-->
**Examples**

```TypeScript
try {
    power.wakeup('wakeup_test');
} catch(err) {
    console.error('wakeup failed, err: ' + err);
}
```

<!--DelEnd-->


## wakeup

```TypeScript
function wakeup(detail: string, mode?: InvokeMode): void | Promise<void>
```

Wakes up a device.

**Since:** 26.1.0

**Required permissions:** ohos.permission.POWER_MANAGER

**Model restriction:** This API can be used only in the stage model.

<!--Device-power-function wakeup(detail: string, mode?: InvokeMode): void | Promise<void>--><!--Device-power-function wakeup(detail: string, mode?: InvokeMode): void | Promise<void>-End-->

**System capability:** SystemCapability.PowerManager.PowerManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| detail | string | Yes | Wakeup reason. The value must be a string. |
| mode | [InvokeMode](arkts-basicservices-power-invokemode-e-sys.md) | No | Invoking mode. You are advised to set this parameter to [InvokeMode.ASYNC](arkts-basicservices-power-invokemode-e-sys.md#async). If this parameter is not set, the default value [InvokeMode.SYNC](arkts-basicservices-power-invokemode-e-sys.md#sync) is used. <br>Default value: InvokeMode.SYNC. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [4900101](../errorcode-power.md#4900101-service-connection-failure) | Failed to connect to the service. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. This API cannot work in car devices. |

<!--Del-->
**Examples**

See [wakeup](#wakeup)

<!--DelEnd-->
