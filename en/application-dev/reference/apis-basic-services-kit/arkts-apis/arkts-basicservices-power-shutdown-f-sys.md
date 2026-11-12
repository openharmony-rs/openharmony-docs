# shutdown (System API)

## Modules to Import

```TypeScript
import { power } from '@kit.BasicServicesKit';
```

## shutdown

```TypeScript
function shutdown(reason: string): void
```

Shuts down the system.

**Since:** 7

**Required permissions:** ohos.permission.REBOOT

<!--Device-power-function shutdown(reason: string): void--><!--Device-power-function shutdown(reason: string): void-End-->

**System capability:** SystemCapability.PowerManager.PowerManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| reason | string | Yes | Shutdown reason. The value must be a string. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Incorrect parameter types; |
| [4900101](../errorcode-power.md#4900101-service-connection-failure) | Failed to connect to the service. |

<!--Del-->
**Examples**

```TypeScript
try {
    power.shutdown('shutdown_test');
} catch(err) {
    console.error('shutdown failed, err: ' + err);
}
```

<!--DelEnd-->


## shutdown

```TypeScript
function shutdown(reason: string, mode?: InvokeMode): void | Promise<void>
```

Shuts down the system.

**Since:** 26.1.0

**Required permissions:** ohos.permission.REBOOT

**Model restriction:** This API can be used only in the stage model.

<!--Device-power-function shutdown(reason: string, mode?: InvokeMode): void | Promise<void>--><!--Device-power-function shutdown(reason: string, mode?: InvokeMode): void | Promise<void>-End-->

**System capability:** SystemCapability.PowerManager.PowerManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| reason | string | Yes | Shutdown reason. The value must be a string. |
| mode | [InvokeMode](arkts-basicservices-power-invokemode-e-sys.md) | No | Invoking mode. You are advised to set this parameter to [InvokeMode.ASYNC](arkts-basicservices-power-invokemode-e-sys.md#async). If this parameter is not set, the default value [InvokeMode.SYNC](arkts-basicservices-power-invokemode-e-sys.md#sync) is used. <br>Default value: InvokeMode.SYNC. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [4900101](../errorcode-power.md#4900101-service-connection-failure) | Failed to connect to the service. |

<!--Del-->
**Examples**

See [shutdown](#shutdown)

<!--DelEnd-->
