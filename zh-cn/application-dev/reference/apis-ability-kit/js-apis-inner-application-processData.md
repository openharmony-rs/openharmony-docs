# ProcessData

进程数据的对象定义。使用接口[on](js-apis-app-ability-appManager.md#appmanageronapplicationstate14)注册生命周期变化监听后，当应用或组件的生命周期变化时，系统通过[ApplicationStateObserver](js-apis-inner-application-applicationStateObserver.md)的onProcessCreated等方法回调给开发者。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块首批接口从API version 14开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```ts
import { appManager } from '@kit.AbilityKit';
```

## 属性

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS-Dyn起始版本：** 14

**ArkTS-Sta起始版本：** 23

| 名称                     | 类型     | 必填 | 说明                       |
| ----------------------- | ---------| ---- | ------------------------- |
| pid         | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 进程ID。                    |
| bundleName  | string   | 是   | 应用包名。                  |
| uid         | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是   | 应用的uid。                  |
| isContinuousTask | boolean   | 是   | 是否为长时任务，true表示是，false表示不是。                 |
| isKeepAlive      | boolean   | 是   | 是否为常驻进程，true表示是，false表示不是。                  |
| state       | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是   | 应用的状态，取值及对应的状态为：<br>0 - 刚创建，<br>1 - 准备就绪，<br>2 - 前台，<br>4 - 后台，<br>5 - 已终止。     |

**示例：**

ArkTS-Dyn示例：

```ts
import { appManager } from '@kit.AbilityKit';

let observerCode = appManager.on('applicationState', {
  onForegroundApplicationChanged(appStateData) {
    console.info(`onForegroundApplicationChanged, appStateData: ${JSON.stringify(appStateData)}.`);
  },
  onAbilityStateChanged(abilityStateData) {
    console.info(`onAbilityStateChanged, abilityStateData: ${JSON.stringify(abilityStateData)}.`);
  },
  onProcessCreated(processData) {
    console.info(`onProcessCreated, processData: ${JSON.stringify(processData)}.`);
  },
  onProcessDied(processData) {
    console.info(`onProcessDied, processData: ${JSON.stringify(processData)}.`);
  },
  onProcessStateChanged(processData) {
    console.info(`onProcessStateChanged, processData.pid : ${processData.pid}.`);
    console.info(`onProcessStateChanged, processData.bundleName : ${processData.bundleName}.`);
    console.info(`onProcessStateChanged, processData.uid : ${processData.uid}.`);
    console.info(`onProcessStateChanged, processData.isContinuousTask : ${processData.isContinuousTask}.`);
    console.info(`onProcessStateChanged, processData.isKeepAlive : ${processData.isKeepAlive}.`);
  },
  onAppStarted(appStateData) {
    console.info(`onAppStarted, appStateData: ${JSON.stringify(appStateData)}.`);
  },
  onAppStopped(appStateData) {
    console.info(`onAppStopped, appStateData: ${JSON.stringify(appStateData)}.`);
  }
});
```
ArkTS-Sta示例：

```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class CustomApplicationStateObserver implements appManager.ApplicationStateObserver {

  public appStateData?: appManager.AppStateData;
  public abilityStateData?: appManager.AbilityStateData;
  public processData?: appManager.ProcessData;

  onForegroundApplicationChanged(appStateData: appManager.AppStateData): void {
    console.info(`onForegroundApplicationChanged, appStateData: ${JSON.stringify(appStateData)}.`);
  }

  onAbilityStateChanged(abilityStateData: appManager.AbilityStateData): void {
    console.info(`onAbilityStateChanged, abilityStateData: ${JSON.stringify(abilityStateData)}.`);
  }

  onProcessCreated(processData: appManager.ProcessData): void {
    console.info(`onProcessCreated, processData: ${JSON.stringify(processData)}.`);
  }

  onProcessDied(processData: appManager.ProcessData): void {
    console.info(`onProcessDied, processData: ${JSON.stringify(processData)}.`);
  }

  onProcessStateChanged(processData: appManager.ProcessData) {
    console.info(`onProcessStateChanged, processData.pid : ${processData.pid}.`);
    console.info(`onProcessStateChanged, processData.bundleName : ${processData.bundleName}.`);
    console.info(`onProcessStateChanged, processData.uid : ${processData.uid}.`);
    console.info(`onProcessStateChanged, processData.isContinuousTask : ${processData.isContinuousTask}.`);
    console.info(`onProcessStateChanged, processData.isKeepAlive : ${processData.isKeepAlive}.`);
  }

  onAppStarted(appStateData: appManager.AppStateData) {
    console.info(`onAppStarted, appStateData: ${JSON.stringify(appStateData)}.`);
  }

  onAppStopped(appStateData: appManager.AppStateData) {
    console.info(`onAppStopped, appStateData: ${JSON.stringify(appStateData)}.`);
  }
};

try {
  let applicationStateObserver=new CustomApplicationStateObserver();
  const observerId = appManager.onApplicationStateChange(applicationStateObserver);
  console.info(`[appManager] observerCode: ${observerId}`);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```