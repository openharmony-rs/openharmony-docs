# onPerception (System API)

## Modules to Import

```TypeScript
import { behaviorAwareness } from '@kit.MultimodalAwarenessKit';
```

## onPerception

```TypeScript
export function onPerception(
    info: SubscribeInfo,
    callback: Callback<PerceptionEvent<BehaviorAwarenessPayload>>
  ): Promise<void>
```

Initiate subscription. The service side registers the subscription relationship with the MSDP and registers the awareness event callback.

When a user performs an action, MSDP filters matches from the awareness event table and pushes them in real time through callbacks. When the same subscription target is subscribed repeatedly, the later callback overrides the previous callback.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-behaviorAwareness-export function onPerception(    info: SubscribeInfo,    callback: Callback<PerceptionEvent<BehaviorAwarenessPayload>>  ): Promise<void>--><!--Device-behaviorAwareness-export function onPerception(    info: SubscribeInfo,    callback: Callback<PerceptionEvent<BehaviorAwarenessPayload>>  ): Promise<void>-End-->

**System capability:** SystemCapability.MultimodalAwareness.DeviceStatus

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | [SubscribeInfo](arkts-multimodalawareness-behaviorawareness-subscribeinfo-i-sys.md) | Yes | Subscription Options. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PerceptionEvent](arkts-multimodalawareness-behaviorawareness-perceptionevent-i-sys.md)&lt;[BehaviorAwarenessPayload](arkts-multimodalawareness-behaviorawareness-behaviorawarenesspayload-i-sys.md)&gt;&gt; | Yes | Callback used to return the awareness event. |

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
