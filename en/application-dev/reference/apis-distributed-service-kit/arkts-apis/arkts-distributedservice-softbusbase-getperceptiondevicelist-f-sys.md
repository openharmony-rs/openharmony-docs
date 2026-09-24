# getPerceptionDeviceList (System API)

## Modules to Import

```TypeScript
```

## getPerceptionDeviceList

```TypeScript
function getPerceptionDeviceList(type: PerceptionType): Promise<PerceptionDeviceInfo[]>
```

Obtains the list of devices discovered by perception scanning. Before calling this API, call [startPerceptionScan](arkts-distributedservice-softbusbase-startperceptionscan-f-sys.md) to start scanning. After the scanning is stopped by calling [stopPerceptionScan](arkts-distributedservice-softbusbase-stopperceptionscan-f-sys.md), the discovered device list is cleared.

**Since:** 26.0.1

**Required permissions:** ohos.permission.ACCESS_SOFTBUS_SYS_HAP and ohos.permission.DISTRIBUTED_DATASYNC

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.SoftBus.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [PerceptionType](arkts-distributedservice-softbusbase-perceptiontype-e-sys.md) | Yes | Perception service type. For details, see [PerceptionType](arkts-distributedservice-softbusbase-perceptiontype-e-sys.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[PerceptionDeviceInfo](arkts-distributedservice-softbusbase-perceptiondeviceinfo-i-sys.md)[]&gt; | Promise used to return the list of devices discovered by perception scanning. Returns an empty array if no devices are discovered or before calling [startPerceptionScan](arkts-distributedservice-softbusbase-startperceptionscan-f-sys.md). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied, need to acquire ohos.permission.ACCESS_SOFTBUS_SYS_HAP and ohos.permission.DISTRIBUTED_DATASYNC. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [2000001](../errorcode-conversation.md#2000001-internal-error) | Internal error. An unexpected system error occurred. |
| 2000002 | Caller error. The caller did not call the API in the specified order. |
| 2000003 | Temporary error. The request failed due to a temporary error and can be retried. |
| 2006001 | Underlying module error. The request failed due to an error in another underlying module and can be retried after a period of time. |
