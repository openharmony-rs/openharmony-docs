# @ohos.app.ability.AppProcessStateObserver (应用进程状态观察者)

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zexin_c-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

定义应用进程状态观察者，用于监听应用内进程的创建和终止。开发者可调用[ApplicationContext.onAppProcessStateChange](js-apis-inner-application-applicationContext.md#applicationcontextonappprocessstatechange)方法传入自定义AppProcessStateObserver来监听应用内进程状态变化，并执行相应操作。例如，在进程创建时初始化资源，在进程终止时清理资源。

**起始版本**：26.1.0

> **说明：**
>
> 本模块接口仅可在Stage模型下使用。

## 导入模块

```ts
import { AppProcessStateObserver } from '@kit.AbilityKit';
```

## AppProcessStateObserver.onProcessCreated

onProcessCreated(processData: ProcessData): void

应用内进程创建时触发回调。

**起始版本**：26.1.0

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| processData | [ProcessData](js-apis-inner-application-processData.md) | 是 | 进程数据，包含进程ID、应用包名、应用uid、进程状态等信息。 |

**示例：**

参见[onProcessDied](#appprocessstateobserveronprocessdied)。

## AppProcessStateObserver.onProcessDied

onProcessDied(processData: ProcessData): void

应用内进程销毁时触发回调。

**起始版本**：26.1.0

**模型约束**：此接口仅可在Stage模型下使用。

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -------- | -------- | -------- | -------- |
| processData | [ProcessData](js-apis-inner-application-processData.md) | 是 | 进程数据，包含进程ID、应用包名、应用uid、进程状态等信息。 |

**示例：**

```ts
import { UIAbility, AppProcessStateObserver, appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let appProcessStateObserver: AppProcessStateObserver = {
  onProcessCreated(processData: appManager.ProcessData) {
    console.info(`onProcessCreated, processData: ${JSON.stringify(processData)}`);
  },
  onProcessDied(processData: appManager.ProcessData) {
    console.info(`onProcessDied, processData: ${JSON.stringify(processData)}`);
  }
};

export default class EntryAbility extends UIAbility {
  onCreate() {
    console.info('MyAbility onCreate');
    // 获取应用上下文
    let applicationContext = this.context.getApplicationContext();
    try {
      // 注册应用内进程状态变化监听
      applicationContext.onAppProcessStateChange(appProcessStateObserver);
    } catch (paramError) {
      console.error(`error code: ${(paramError as BusinessError).code}, error msg: ${(paramError as BusinessError).message}`);
    }
    console.info('Register appProcessStateObserver');
  }

  // 不再需要或应用退出时取消监听
  onDestroy() {
    // 获取应用上下文
    let applicationContext = this.context.getApplicationContext();
    try {
      applicationContext.offAppProcessStateChange(appProcessStateObserver);
    } catch (paramError) {
      console.error(`error: ${(paramError as BusinessError).code}, ${(paramError as BusinessError).message}`);
    }
  }
}
```
