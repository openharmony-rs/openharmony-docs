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

Enable the cross-thread data transfer feature of [EventHub](arkts-ability-eventhub-c.md) in a [Context](arkts-ability-context-c.md) object on the main thread, convert the Context object to a [SendableContext](arkts-ability-sendablecontext-i.md) object, and send the SendableContext object to the [Worker](../../apis-arkts/arkts-apis/arkts-arkts-worker-n.md) thread.

```TypeScript
import { common, sendableContextManager } from '@kit.AbilityKit';
import { worker } from '@kit.ArkTS';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN = 0x0000;

@Sendable
export class SendableObject {
  constructor(sendableContext: sendableContextManager.SendableContext, contextName: string) {
    this.sendableContext = sendableContext;
    this.contextName = contextName;
  }

  sendableContext: sendableContextManager.SendableContext;
  contextName: string;
}

@Entry
@Component
struct Index {
  @State context: common.Context | undefined = this.getUIContext().getHostContext();
  worker1: worker.ThreadWorker = new worker.ThreadWorker('entry/ets/workers/Worker.ets');

  aboutToAppear(): void {
    let context: common.Context = this.context as common.Context;
    context.eventHub.on('event1', this.eventFunc);
    context.eventHub.emit('event1', 'xingming', 22);
  }

  eventFunc(name: string, age: number) {
    hilog.info(DOMAIN, 'testTag', 'name %{public}s age %{public}d', name, age);
  }

  build() {
    Column() {
      Row() {
        Button('thread 1')
          .size({ width: 100, height: 100 })
          .onClick(() => {
            if (this.context == undefined) {
              return;
            }
            sendableContextManager.setEventHubMultithreadingEnabled(this.context, true);
            let sendableContext: sendableContextManager.SendableContext =
              sendableContextManager.convertFromContext(this.context);
            let object: SendableObject = new SendableObject(sendableContext, 'BaseContext');
            this.worker1.postMessageWithSharedSendable(object);
          })
      }
    }
  }
}
```

After receiving the [SendableContext](arkts-ability-sendablecontext-i.md) object on the [Worker](../../apis-arkts/arkts-apis/arkts-arkts-worker-n.md) thread, convert it to a [Context](arkts-ability-context-c.md) object. Then, enable the cross-thread data transfer feature of [EventHub](arkts-ability-eventhub-c.md) in the Context object on the Worker thread, and send a message back to the main thread using this feature.

```TypeScript
import { ErrorEvent, MessageEvents, ThreadWorkerGlobalScope, worker } from '@kit.ArkTS';
import { common, sendableContextManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

const DOMAIN = 0x0000;

@Sendable
export class SendableObject {
  constructor(sendableContext: sendableContextManager.SendableContext, contextName: string) {
    this.sendableContext = sendableContext;
    this.contextName = contextName;
  }

  sendableContext: sendableContextManager.SendableContext;
  contextName: string;
}

const workerPort: ThreadWorkerGlobalScope = worker.workerPort;

workerPort.onmessage = (e: MessageEvents) => {
  let object: SendableObject = e.data;
  let sendableContext: sendableContextManager.SendableContext = object.sendableContext;
  if (object.contextName == 'BaseContext') {
    let context: common.Context = sendableContextManager.convertToContext(sendableContext);
    sendableContextManager.setEventHubMultithreadingEnabled(context, true);
    context.eventHub.emit('event1', 'xingming', 40);
  }
};

workerPort.onmessageerror = (e: MessageEvents) => {
  hilog.error(DOMAIN, 'testTag', '%{public}s', 'onmessageerror');
};

workerPort.onerror = (e: ErrorEvent) => {
  hilog.error(DOMAIN, 'testTag', '%{public}s', 'onerror');
};
```
