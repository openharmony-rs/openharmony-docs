# setPowerMode (System API)

## Modules to Import

```TypeScript
import { power } from '@kit.BasicServicesKit';
```

## setPowerMode

```TypeScript
function setPowerMode(mode: DevicePowerMode, callback: AsyncCallback<void>): void
```

Sets the power mode of a device. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.POWER_OPTIMIZATION

<!--Device-power-function setPowerMode(mode: DevicePowerMode, callback: AsyncCallback<void>): void--><!--Device-power-function setPowerMode(mode: DevicePowerMode, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.PowerManager.PowerManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [DevicePowerMode](arkts-basicservices-power-devicepowermode-e.md) | Yes | Power mode. The value must be an enum. |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback invoked to return the result.<br> If the power mode is successfully set, **err** is **undefined**; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [203](../../errorcode-universal.md#203-system-function-prohibited-by-enterprise-management-policies) | This function is prohibited by enterprise management policies.<br>**Applicable version:** 26.1.0 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Parameter verification failed. |
| [4900301](../errorcode-power.md#4900301-power-mode-setting-failed) | Setting the power mode failed.<br>**Applicable version:** 23 and later |

<!--Del-->
**Examples**

```TypeScript
power.setPowerMode(power.DevicePowerMode.MODE_PERFORMANCE, (err: Error) => {
    if (typeof err === 'undefined') {
        console.info('set power mode to MODE_PERFORMANCE');
    } else {
        console.error('set power mode failed, err: ' + err);
    }
});
```

<!--DelEnd-->


## setPowerMode

```TypeScript
function setPowerMode(mode: DevicePowerMode): Promise<void>
```

Sets the power mode of a device. This API uses a promise to return the result. To set both the power mode and the sub-mode, use [setPowerMode(mode, subMode)](#setpowermode-3).

**Since:** 9

**Required permissions:** ohos.permission.POWER_OPTIMIZATION

<!--Device-power-function setPowerMode(mode: DevicePowerMode): Promise<void>--><!--Device-power-function setPowerMode(mode: DevicePowerMode): Promise<void>-End-->

**System capability:** SystemCapability.PowerManager.PowerManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [DevicePowerMode](arkts-basicservices-power-devicepowermode-e.md) | Yes | Power mode. The value must be an enum. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [203](../../errorcode-universal.md#203-system-function-prohibited-by-enterprise-management-policies) | This function is prohibited by enterprise management policies.<br>**Applicable version:** 26.1.0 and later |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Parameter verification failed. |
| [4900301](../errorcode-power.md#4900301-power-mode-setting-failed) | Setting the power mode failed.<br>**Applicable version:** 23 and later |

<!--Del-->
**Examples**

```TypeScript
power.setPowerMode(power.DevicePowerMode.MODE_PERFORMANCE)
.then(() => {
    console.info('set power mode to MODE_PERFORMANCE');
})
.catch((err : Error)=> {
    console.error('set power mode failed, err: ' + err);
});
```

<!--DelEnd-->


## setPowerMode

```TypeScript
function setPowerMode(mode: DevicePowerMode, subMode?: DevicePowerSubMode): Promise<void>
```

Sets the power mode and sub-mode of a device. This API uses a promise to return the result. To set the power mode only (without sub-mode), use [setPowerMode(promise)](#setpowermode-2) or [setPowerMode(callback)](#setpowermode-1).

**Since:** 26.1.0

**Required permissions:** ohos.permission.POWER_OPTIMIZATION

**Model restriction:** This API can be used only in the stage model.

<!--Device-power-function setPowerMode(mode: DevicePowerMode, subMode?: DevicePowerSubMode): Promise<void>--><!--Device-power-function setPowerMode(mode: DevicePowerMode, subMode?: DevicePowerSubMode): Promise<void>-End-->

**System capability:** SystemCapability.PowerManager.PowerManager.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [DevicePowerMode](arkts-basicservices-power-devicepowermode-e.md) | Yes | Power mode. The value must be an enum. |
| subMode | [DevicePowerSubMode](arkts-basicservices-power-devicepowersubmode-e.md) | No | Power sub-mode. The value must be an enum. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [203](../../errorcode-universal.md#203-system-function-prohibited-by-enterprise-management-policies) | This function is prohibited by enterprise management policies. |
| [4900101](../errorcode-power.md#4900101-service-connection-failure) | Failed to connect to the service. |
| [4900301](../errorcode-power.md#4900301-power-mode-setting-failed) | Failed to set the power mode. Possible causes: <br>1. The power mode switching constraint is not met; <br>2. The power mode does not support the sub-mode, or the sub-mode does not match the power mode. |

<!--Del-->
**Examples**

```TypeScript
power.setPowerMode(power.DevicePowerMode.MODE_PERFORMANCE, (err: Error) => {
    if (typeof err === 'undefined') {
        console.info('set power mode to MODE_PERFORMANCE');
    } else {
        console.error('set power mode failed, err: ' + err);
    }
});
```

```TypeScript
power.setPowerMode(power.DevicePowerMode.MODE_PERFORMANCE)
.then(() => {
    console.info('set power mode to MODE_PERFORMANCE');
})
.catch((err : Error)=> {
    console.error('set power mode failed, err: ' + err);
});
```

<!--DelEnd-->
