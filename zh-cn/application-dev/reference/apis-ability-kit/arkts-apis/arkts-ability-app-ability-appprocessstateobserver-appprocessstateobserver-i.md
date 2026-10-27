# AppProcessStateObserver

```TypeScript
declare interface AppProcessStateObserver
```

定义一个观察者来监听应用程序中的进程状态变化。它可以用作中的输入参数[ApplicationContext.onAppProcessStateChange](arkts-ability-applicationcontext-c.md#onappprocessstatechange)来监听应用程序中进程的创建和终止。

**起始版本：** 26.1.0

<!--Device-unnamed-declare interface AppProcessStateObserver--><!--Device-unnamed-declare interface AppProcessStateObserver-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { AppProcessStateObserver } from '@kit.AbilityKit';
```

## onProcessCreated

```TypeScript
onProcessCreated(processData: ProcessData): void
```

在应用程序中创建进程时调用。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AppProcessStateObserver-onProcessCreated(processData: ProcessData): void--><!--Device-AppProcessStateObserver-onProcessCreated(processData: ProcessData): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| processData | [ProcessData](arkts-ability-processdata-c.md) | 是 | 流程数据。 |

## onProcessDied

```TypeScript
onProcessDied(processData: ProcessData): void
```

当应用程序中的进程被销毁时调用。

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AppProcessStateObserver-onProcessDied(processData: ProcessData): void--><!--Device-AppProcessStateObserver-onProcessDied(processData: ProcessData): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| processData | [ProcessData](arkts-ability-processdata-c.md) | 是 | 流程数据。 |
