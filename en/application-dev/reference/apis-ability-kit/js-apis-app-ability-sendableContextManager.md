# @ohos.app.ability.sendableContextManager (Sendable Context Management)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zhangyafei-echo; @xuzhihao666-->
<!--Designer: @zhangyafei-echo-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

The sendableContextManager module provides APIs for converting between Context and [SendableContext](js-apis-inner-application-sendableContext.md) objects.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The APIs of this module can be used only in the stage model.

## When to Use

This module is used to transfer data between concurrent ArkTS instances (including the main thread and the worker thread of TaskPool or Worker).

When the main thread transfers sendable data (data that complies with the [Sendable protocol](../../arkts-utils/arkts-sendable.md#sendable-protocol)) to the child thread (such as the TaskPool or Worker thread), the conversion between the Context and SendableContext is required. The process is as follows:
- Conversion from Context to SendableContext for the main thread to transfer sendable data to the child thread.
- Conversion from SendableContext to Context for the child thread to use the sendable data.

The Context here is different from that created by [createModuleContext](./js-apis-app-ability-application.md#applicationcreatemodulecontext12). The differences are as follows:
- Context involved in the conversion: ArkTS concurrent instances hold different application-side Context instances that correspond to the same underlying Context object. When the Context properties and methods in an instance are modified, the Context properties and methods in the related instances are modified accordingly. The eventHub attribute in the Context instance is special. The eventHub objects in different instances are independent of each other and cannot be used across ArkTS instances. 

- Context created using [createModuleContext](./js-apis-app-ability-application.md#applicationcreatemodulecontext12): ArkTS concurrent instances hold different application-side Context objects that correspond to different underlying Context objects.

## Constraints

The Context types used in the conversion must be the same. For example, if the main thread uses [convertFromContext](#sendablecontextmanagerconvertfromcontext) to convert the [UIAbilityContext](js-apis-inner-application-uiAbilityContext.md) to the SendableContext, the child thread must call [convertToUIAbilityContext](#sendablecontextmanagerconverttouiabilitycontext) to convert the received SendableContext to the [UIAbilityContext](js-apis-inner-application-uiAbilityContext.md).

Currently, the following types of Context support conversion: [Context](js-apis-inner-application-context.md), [ApplicationContext](js-apis-inner-application-applicationContext.md), [AbilityStageContext](js-apis-inner-application-abilityStageContext.md), and [UIAbilityContext](js-apis-inner-application-uiAbilityContext.md).

## Modules to Import

```ts
import { sendableContextManager } from '@kit.AbilityKit';
```

## SendableContext

type SendableContext = _SendableContext

Defines the Sendable context. It complies with the [Sendable protocol](../../arkts-utils/arkts-sendable.md#sendable-protocol) and inherits from [lang.ISendable](../apis-arkts/js-apis-arkts-lang.md#langisendable).

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Atomic service API**: This API can be used in atomic services since API version 12.

| Type| Description|
| --- | --- |
| [_SendableContext](js-apis-inner-application-sendableContext.md) | Sendable context, which can be converted to a Context object to implement data transmission between concurrent ArkTS instances (including the main thread and the worker thread of TaskPool or Worker).|

## sendableContextManager.convertFromContext

convertFromContext(context: common.Context): SendableContext

Converts a Context object to a SendableContext object.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| ------- | ------- | ------- | ------- |
| context | [common.Context](js-apis-inner-application-context.md) | Yes| Context object. The Context base class, and its child classes [ApplicationContext](js-apis-inner-application-applicationContext.md), [AbilityStageContext](js-apis-inner-application-abilityStageContext.md), and [UIAbilityContext](js-apis-inner-application-uiAbilityContext.md) are supported.|

**Return value**

| Type| Description|
| -------- | -------- |
| SendableContext | [SendableContext](js-apis-inner-application-sendableContext.md) object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | ------- |
| 401     | If the input parameter invalid. Possible causes: 1.Incorrect parameter types; 2.Parameter verification failed. |

**Example**

```ts
import { AbilityConstant, UIAbility, Want, sendableContextManager } from '@kit.AbilityKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { worker } from '@kit.ArkTS';

@Sendable
export class SendableObject {
  constructor(sendableContext: sendableContextManager.SendableContext) {
    this.sendableContext = sendableContext;
  }

  sendableContext: sendableContextManager.SendableContext;
  // other sendable object
}

export default class EntryAbility extends UIAbility {
  worker: worker.ThreadWorker = new worker.ThreadWorker('entry/ets/workers/Worker.ets');

  onCreate(want: Want, launchParam: AbilityConstant.LaunchParam): void {
    hilog.info(0x0000, 'testTag', '%{public}s', 'Ability onCreate');

    // convert and post
    try {
      let sendableContext: sendableContextManager.SendableContext =
        sendableContextManager.convertFromContext(this.context);
      let object: SendableObject = new SendableObject(sendableContext);
      hilog.info(0x0000, 'testTag', '%{public}s', 'Ability post message');
      this.worker.postMessageWithSharedSendable(object);
    } catch (error) {
      hilog.error(0x0000, 'testTag', 'convertFromContext failed %{public}s', JSON.stringify(error));
    }
  }
}
```

## sendableContextManager.convertToContext

convertToContext(sendableContext: SendableContext): common.Context

Converts a SendableContext object to a Context object.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| ------- | ------- | ------- | ------- |
| sendableContext | [SendableContext](js-apis-inner-application-sendableContext.md) | Yes| SendableContext object.|

**Return value**

| Type| Description|
| -------- | -------- |
| common.Context | [Context](js-apis-inner-application-context.md) object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | ------- |
| 401     | If the input parameter invalid. Possible causes: 1.Incorrect parameter types; 2.Parameter verification failed. |

**Example**

Context passed by the main thread:
```ts
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
      let context: common.Context = this.context as common.Context;
      let sendableContext: sendableContextManager.SendableContext = sendableContextManager.convertFromContext(context);
      let object: SendableObject = new SendableObject(sendableContext, 'BaseContext');
      hilog.info(0x0000, 'testTag', '%{public}s', 'Ability post message');
      this.worker.postMessageWithSharedSendable(object);
    } catch (error) {
      hilog.error(0x0000, 'testTag', 'convertFromContext failed %{public}s', JSON.stringify(error));
    }
  }
}
```

Context received by the Worker thread:
```ts
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
  if (object.contextName == 'BaseContext') {
    hilog.info(0x0000, 'testTag', '%{public}s', 'convert to context.');
    try {
      let context: common.Context = sendableContextManager.convertToContext(sendableContext);
      // Obtain the sandbox path after obtaining the Context object.
      hilog.info(0x0000, 'testTag', 'worker context.databaseDir: %{public}s', context.databaseDir);
    } catch (error) {
      hilog.error(0x0000, 'testTag', 'convertToContext failed %{public}s', JSON.stringify(error));
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

## sendableContextManager.convertToApplicationContext

convertToApplicationContext(sendableContext: SendableContext): common.ApplicationContext

Converts a SendableContext object to an ApplicationContext object.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| ------- | ------- | ------- | ------- |
| sendableContext | [SendableContext](js-apis-inner-application-sendableContext.md) | Yes| SendableContext object.|

**Return value**

| Type| Description|
| -------- | -------- |
| common.ApplicationContext | [ApplicationContext](js-apis-inner-application-applicationContext.md) object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | ------- |
| 401     | If the input parameter invalid. Possible causes: 1.Incorrect parameter types; 2.Parameter verification failed. |

**Example**

Context passed by the main thread:
```ts
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
      let context: common.Context = this.context as common.Context;
      let applicationContext = context.getApplicationContext();
      let sendableContext: sendableContextManager.SendableContext =
        sendableContextManager.convertFromContext(applicationContext);
      let object: SendableObject = new SendableObject(sendableContext, 'ApplicationContext');
      hilog.info(0x0000, 'testTag', '%{public}s', 'Ability post message');
      this.worker.postMessageWithSharedSendable(object);
    } catch (error) {
      hilog.error(0x0000, 'testTag', 'convertFromContext failed %{public}s', JSON.stringify(error));
    }
  }
}
```

Context received by the Worker thread:
```ts
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
  if (object.contextName == 'ApplicationContext') {
    hilog.info(0x0000, 'testTag', '%{public}s', 'convert to application context.');
    try {
      let context: common.ApplicationContext = sendableContextManager.convertToApplicationContext(sendableContext);
      // Obtain the sandbox path after obtaining the Context object.
      hilog.info(0x0000, 'testTag', 'worker context.databaseDir: %{public}s', context.databaseDir);
    } catch (error) {
      hilog.error(0x0000, 'testTag', 'convertToApplicationContext failed %{public}s', JSON.stringify(error));
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

## sendableContextManager.convertToAbilityStageContext

convertToAbilityStageContext(sendableContext: SendableContext): common.AbilityStageContext

Converts a SendableContext object to an AbilityStageContext object.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| ------- | ------- | ------- | ------- |
| sendableContext | [SendableContext](js-apis-inner-application-sendableContext.md) | Yes| SendableContext object.|

**Return value**

| Type| Description|
| -------- | -------- |
| common.AbilityStageContext | [AbilityStageContext](js-apis-inner-application-abilityStageContext.md) object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | ------- |
| 401     | If the input parameter invalid. Possible causes: 1.Incorrect parameter types; 2.Parameter verification failed. |

**Example**

Context passed by the main thread:
```ts
import { UIAbility, sendableContextManager } from '@kit.AbilityKit';
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

  onCreate(): void {
    hilog.info(0x0000, 'testTag', '%{public}s', 'AbilityStage onCreate');

    // convert and post
    try {
      let sendableContext: sendableContextManager.SendableContext =
        sendableContextManager.convertFromContext(this.context);
      let object: SendableObject = new SendableObject(sendableContext, 'AbilityStageContext');
      hilog.info(0x0000, 'testTag', '%{public}s', 'AbilityStage post message');
      this.worker.postMessageWithSharedSendable(object);
    } catch (error) {
      hilog.error(0x0000, 'testTag', 'convertFromContext failed %{public}s', JSON.stringify(error));
    }
  }
}
```

Context received by the Worker thread:
```ts
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
  if (object.contextName == 'AbilityStageContext') {
    hilog.info(0x0000, 'testTag', '%{public}s', 'convert to abilitystage context.');
    try {
      let context: common.AbilityStageContext = sendableContextManager.convertToAbilityStageContext(sendableContext);
      // Obtain the sandbox path after obtaining the Context object.
      hilog.info(0x0000, 'testTag', 'worker context.databaseDir: %{public}s', context.databaseDir);
    } catch (error) {
      hilog.error(0x0000, 'testTag', 'convertToAbilityStageContext failed %{public}s', JSON.stringify(error));
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

## sendableContextManager.convertToUIAbilityContext

convertToUIAbilityContext(sendableContext: SendableContext): common.UIAbilityContext

Converts a SendableContext object to a UIAbilityContext object.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Parameters**

| Name| Type| Mandatory| Description|
| ------- | ------- | ------- | ------- |
| sendableContext | [SendableContext](js-apis-inner-application-sendableContext.md) | Yes| SendableContext object.|

**Return value**

| Type| Description|
| -------- | -------- |
| common.UIAbilityContext | [UIAbilityContext](js-apis-inner-application-uiAbilityContext.md) object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | ------- |
| 401     | If the input parameter invalid. Possible causes: 1.Incorrect parameter types; 2.Parameter verification failed. |

**Example**

Context passed by the main thread:
```ts
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
      hilog.error(0x0000, 'testTag', 'convertFromContext failed %{public}s', JSON.stringify(error));
    }
  }
}
```

Context received by the Worker thread:
```ts
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
    hilog.info(0x0000, 'testTag', '%{public}s', 'convert to uiability context.');
    try {
      let context: common.UIAbilityContext = sendableContextManager.convertToUIAbilityContext(sendableContext);
      // Obtain the sandbox path after obtaining the Context object.
      hilog.info(0x0000, 'testTag', 'worker context.databaseDir: %{public}s', context.databaseDir);
    } catch (error) {
      hilog.error(0x0000, 'testTag', 'convertToUIAbilityContext failed %{public}s', JSON.stringify(error));
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
