# setEventHubMultithreadingEnabled

## Modules to Import

```TypeScript
import { sendableContextManager } from '@kit.AbilityKit';
```

## setEventHubMultithreadingEnabled

```TypeScript
function setEventHubMultithreadingEnabled(context: common.Context, enabled: boolean): void
```

Enables the cross-thread data transfer feature of [EventHub](arkts-ability-eventhub-c.md) in Context.

> **NOTE:** 
> 
> - When multiple Context objects communicate, you need to call this API to set each Context object to support EventHub cross-thread data transfer.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | [common.Context](arkts-ability-common-context-t.md) | Yes | Context object. For details about the serialization data types supported by Eventhub, see [Sequenceable Data Types](../../../reference/apis-arkts/js-apis-taskpool.md#sequenceable-data-types). The data size cannot exceed 16 MB. |
| enabled | boolean | Yes | Whether to enable the cross-thread data transfer feature.<br>- **true**: The cross-thread data transfer feature is enabled, and data is passed by reference.<br>- **false**: The cross-thread data transfer feature is disabled. Data is passed through serialization, which means that the data of the sender thread is independent of that of the receiver thread. |

**Examples**

```TypeScript
Enable the cross-thread data transfer feature of [EventHub](arkts-ability-eventhub-c.md) in a [Context](arkts-ability-context-c.md) object on the main thread, convert the Context object to a [SendableContext](arkts-ability-sendablecontext-i.md) object, and send the SendableContext object to the [Worker](../../apis-arkts/arkts-apis/arkts-arkts-worker-n.md) thread.
```

```TypeScript
After receiving the [SendableContext](arkts-ability-sendablecontext-i.md) object on the [Worker](../../apis-arkts/arkts-apis/arkts-arkts-worker-n.md) thread, convert it to a [Context](arkts-ability-context-c.md) object. Then, enable the cross-thread data transfer feature of [EventHub](arkts-ability-eventhub-c.md) in the Context object on the Worker thread, and send a message back to the main thread using this feature.
```
