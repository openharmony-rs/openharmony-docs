# setEventHubMultithreadingEnabled

## 导入模块

```TypeScript
import { sendableContextManager } from '@kit.AbilityKit';
```

## setEventHubMultithreadingEnabled

```TypeScript
function setEventHubMultithreadingEnabled(context: common.Context, enabled: boolean): void
```

设置[Context](arkts-ability-context-t.md)中的[EventHub](arkts-ability-eventhub-c.md)是否启用跨线程通信能力。
> **说明：**  
>  
> - 当多个Context进行通信时，需要调用该接口设置每个Context都支持EventHub跨线程数据传递功能。

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-sendableContextManager-function setEventHubMultithreadingEnabled(context: common.Context, enabled: boolean): void--><!--Device-sendableContextManager-function setEventHubMultithreadingEnabled(context: common.Context, enabled: boolean): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| context | common.Context | 是 | Context对象。其中，Eventhub支持传递的序列化数据类型参见[序列化支持的类型](../../../reference/apis-arkts/js-apis-taskpool.md#序列化支持类型)，数据大小不超过16MB。 |
| enabled | boolean | 是 | 表示是否启用Context的EventHub跨线程通信能力。true表示启用，false表示禁用。 |

**示例：**

主线程启用[Context](./js-apis-inner-application-context.md)中[EventHub](./js-apis-inner-application-eventHub.md)的跨线程通信能力，并将Context转换为[SendableContext](js-apis-inner-application-sendableContext.md)后发送到[Worker](../apis-arkts/js-apis-worker.md)线程。

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

[Worker](../apis-arkts/js-apis-worker.md)线程接收到[SendableContext](js-apis-inner-application-sendableContext.md)后，将其转换为[Context](./js-apis-inner-application-context.md)。然后，在Worker线程内，启用Context中[EventHub](./js-apis-inner-application-eventHub.md)的跨线程通信能力，并通过该功能向主线程发送消息。

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

