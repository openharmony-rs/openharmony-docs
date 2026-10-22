# offPerception (System API)

## Modules to Import

```TypeScript
import { behaviorAwareness } from '@kit.MultimodalAwarenessKit';
```

## offPerception

```TypeScript
export function offPerception(
    callback?: Callback<PerceptionEvent<BehaviorAwarenessPayload>>
  ): Promise<void>
```

The service cancels the subscription relationship on the MSDP.

If a callback is passed, only the subscriptions that match the callback are canceled. If no callback is passed, all subscriptions under the current package are canceled.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-behaviorAwareness-export function offPerception(    callback?: Callback<PerceptionEvent<BehaviorAwarenessPayload>>  ): Promise<void>--><!--Device-behaviorAwareness-export function offPerception(    callback?: Callback<PerceptionEvent<BehaviorAwarenessPayload>>  ): Promise<void>-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PerceptionEvent](arkts-multimodalawareness-behaviorawareness-perceptionevent-i-sys.md)&lt;[BehaviorAwarenessPayload](arkts-multimodalawareness-behaviorawareness-behaviorawarenesspayload-i-sys.md)&gt;&gt; | No | Callback used to return Awareness event. Used to clear the awareness of all subscriptions Events. <br>Default value: If this parameter is not specified, all subscriptions of the current package are canceled. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application uses the system API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: <br>1. The hardware does not support the capability. <br>2. The chip does not support the capability. <br>3. A dependent service feature is not supported. |
| [32500001](../errorcode-deviceStatus.md#32500001-abnormal-service) | Service exception. |
| [32500003](../errorcode-deviceStatus.md#32500003-unsubscription-failed) | Unsubscription failed. |
