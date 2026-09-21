# startPerceptionAdv (System API)

## Modules to Import

```TypeScript
```

## startPerceptionAdv

```TypeScript
function startPerceptionAdv(type: PerceptionType, customData?: ArrayBuffer): Promise<void>
```

Starts perception advertising or updates the custom payload carried in the advertising of the current owner. After the advertising is started, surrounding devices that are scanning can discover the current device.

**Since:** 26.0.1

**Required permissions:** ohos.permission.ACCESS_SOFTBUS_SYS_HAP and ohos.permission.DISTRIBUTED_DATASYNC

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.SoftBus.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | [PerceptionType](arkts-distributedservice-softbusbase-perceptiontype-e-sys.md) | Yes | Perception service type. For details, see [PerceptionType](arkts-distributedservice-softbusbase-perceptiontype-e-sys.md). |
| customData | ArrayBuffer | No | Custom payload carried in the advertising. The data structure is defined by the application layer protocol. If the length exceeds 5 bytes, an error is thrown.<br>The maximum length is 5 bytes. Default value: An empty ArrayBuffer. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied, need to acquire ohos.permission.ACCESS_SOFTBUS_SYS_HAP and ohos.permission.DISTRIBUTED_DATASYNC. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |
| [2000001](../errorcode-conversation.md#2000001-internal-error) | Internal error. An unexpected system error occurred. |
| 2000003 | Temporary error. The request failed due to a temporary error and can be retried. |
| 2006001 | Underlying module error. The request failed due to an error in another underlying module and can be retried after a period of time. |
