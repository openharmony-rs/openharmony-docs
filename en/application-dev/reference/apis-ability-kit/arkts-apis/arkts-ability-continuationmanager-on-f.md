# on

## Modules to Import

```TypeScript
import { continuationManager } from '@kit.AbilityKit';
```

## on('deviceSelected')

```TypeScript
function on(type: 'deviceSelected', token: number, callback: Callback<Array<ContinuationResult>>): void
```

Subscribes to device connection events. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 22

**Substitutes:** [on](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#ondevicestatechange)(type: 'deviceStateChange', callback: Callback&lt;{ action: DeviceStateChange; device: DeviceBasicInfo; }&gt;)

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.DistributedAbilityManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'deviceSelected' | Yes | Event type. The value is fixed at **deviceSelected**. |
| token | number | Yes | Token obtained after the registration of the continuation management service. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;[ContinuationResult](arkts-ability-continuationmanager-continuationresult-t.md)&gt;&gt; | Yes | Callback invoked when a device is selected from the device list provided by the device selection module. This callback returns the device ID, type, and name. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [16600001](../errorcode-DistributedSchedule.md#16600001-the-system-ability-works-abnormally) | The system ability works abnormally. |
| [16600002](../errorcode-DistributedSchedule.md#16600002-the-specified-token-or-callback-is-not-registered) | The specified token or callback is not registered. |
| [16600004](../errorcode-DistributedSchedule.md#16600004-the-specified-callback-has-been-registered) | The specified callback has been registered. |


## on('deviceUnselected')

```TypeScript
function on(type: 'deviceUnselected', token: number, callback: Callback<Array<ContinuationResult>>): void
```

Subscribes to device disconnection events. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 22

**Substitutes:** [on](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#ondevicestatechange)(type: 'deviceStateChange', callback: Callback&lt;{ action: DeviceStateChange; device: DeviceBasicInfo; }&gt;)

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Ability.DistributedAbilityManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'deviceUnselected' | Yes | Event type. The value is fixed at **deviceUnselected**. |
| token | number | Yes | Token obtained after the registration of the continuation management service. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;[ContinuationResult](arkts-ability-continuationmanager-continuationresult-t.md)&gt;&gt; | Yes | Callback invoked when a device is unselected from the device list provided by the device selection module. This callback returns the device ID, type, and name. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [16600001](../errorcode-DistributedSchedule.md#16600001-the-system-ability-works-abnormally) | The system ability works abnormally. |
| [16600002](../errorcode-DistributedSchedule.md#16600002-the-specified-token-or-callback-is-not-registered) | The specified token or callback is not registered. |
| [16600004](../errorcode-DistributedSchedule.md#16600004-the-specified-callback-has-been-registered) | The specified callback has been registered. |


## on('deviceConnect')

```TypeScript
function on(type: 'deviceConnect', callback: Callback<ContinuationResult>): void
```

Subscribes to device connection events. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [on](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#ondevicestatechange)(type: 'deviceStateChange', callback: Callback&lt;{ action: DeviceStateChange; device: DeviceBasicInfo; }&gt;)

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.DistributedAbilityManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'deviceConnect' | Yes | Event type. The value is fixed at **deviceConnect**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ContinuationResult](arkts-ability-continuationmanager-continuationresult-t.md)&gt; | Yes | Callback invoked when a device is selected from the device list provided by the device selection module. This callback returns the device ID, type, and name. |


## on('deviceDisconnect')

```TypeScript
function on(type: 'deviceDisconnect', callback: Callback<string>): void
```

Subscribes to device disconnection events. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [on](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#ondevicestatechange)(type: 'deviceStateChange', callback: Callback&lt;{ action: DeviceStateChange; device: DeviceBasicInfo; }&gt;)

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.DistributedAbilityManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'deviceDisconnect' | Yes | Event type. The value is fixed at **deviceDisconnect**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;string&gt; | Yes | Callback invoked when a device is unselected from the device list provided by the device selection module. This callback returns the device ID. |
