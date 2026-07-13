# convertToUIAbilityContext

## convertToUIAbilityContext

```TypeScript
function convertToUIAbilityContext(sendableContext: SendableContext): common.UIAbilityContext
```

将SendableContext对象转换为UIAbilityContext。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sendableContext | SendableContext | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| common.UIAbilityContext | [UIAbilityContext](arkts-ability-uiabilitycontext-c.md)object. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | If the input parameter invalid. Possible causes: 1.Incorrect parameter types;2.Parameter verification failed. |

**示例：**

主线程传递Context：

```TypeScript
import { AbilityConstant, UIAbility, Want, common, sendableContextManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { worker } from '@kit.ArkTS';

@Sendable
export class SendableObject {
  constructor(sendableContext: sendableContextManager.SendableContext, contextName: string) {
    this.sendableContext = sendableContext;
    this.contextName = contextName;
  }

  sendableContext: sendableContextManager.SendableContext;
  contextName: string;
}

export default class EntryAbility extends UIAbility {
  worker: worker.ThreadWorker = new worker.ThreadWorker('entry/ets/workers/Worker.ets');

  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onCreate');

    // convert and post
    try {
      let sendableContext: sendableContextManager.SendableContext =
        sendableContextManager.convertFromContext(this.context);
      let object: SendableObject = new SendableObject(sendableContext, 'EntryAbilityContext');
      hilog.info(0x0000, 'testTag', '%{public}s', 'Ability post message');
      this.worker.postMessageWithSharedSendable(object);
    } catch (error) {
      hilog.error(
        0x0000, 'testTag', `convertFromContext failed, error code: ${error.code}, error msg: ${error.message}`);
    }
  }
}

```

Worker线程接收Context：

```TypeScript
import { ErrorEvent, MessageEvents, ThreadWorkerGlobalScope, worker } from '@kit.ArkTS';
import { common, sendableContextManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

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
  if (object.contextName == 'EntryAbilityContext') {
    hilog.info(0x0000, 'testTag', '%{public}s', 'convert to UIAbility context.');
    try {
      let context: common.UIAbilityContext = sendableContextManager.convertToUIAbilityContext(sendableContext);
      // 获取context后获取沙箱路径
      hilog.info(0x0000, 'testTag', 'worker context.databaseDir: %{public}s', context.databaseDir);
    } catch (error) {
      hilog.error(0x0000,
        'testTag', `convertToUIAbilityContext failed, error code: ${error.code}, error msg: ${error.message}`);
    }
  }
}

workerPort.onmessageerror = (e: MessageEvents) => {
  hilog.info(0x0000, 'testTag', '%{public}s', 'onmessageerror');
}

workerPort.onerror = (e: ErrorEvent) => {
  hilog.info(0x0000, 'testTag', '%{public}s', 'onerror');
}

```

