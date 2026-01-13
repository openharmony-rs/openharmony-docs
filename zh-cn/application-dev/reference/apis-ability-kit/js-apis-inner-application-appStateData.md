# AppStateData

定义应用状态信息，可以通过[appManager.on('applicationState')](./js-apis-app-ability-appManager.md#appmanageronapplicationstate14)获取当前应用的相关信息。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块首批接口从API version 14 开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## 导入模块

```ts
import { appManager } from '@kit.AbilityKit';
```

## 属性

**系统能力**：SystemCapability.Ability.AbilityRuntime.Core

**ArkTS-Dyn起始版本：** 14

**ArkTS-Sta起始版本：** 23

| 名称                      | 类型   | 必填  | 说明       |
| ------------------------- | ------ | ---- | --------- |
| bundleName  | string | 是   | Bundle名称。 |
| uid          | ArkTS-Dyn: number<br>ArkTS-Sta: int | 是   | 应用程序的uid。   |
| state        | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是   | 应用状态。<br>0：初始化状态，应用正在初始化。<br>1：就绪状态，应用已初始化完毕。<br>2：前台状态，应用位于前台。<br>3：获焦状态。（预留状态，当前暂不支持）。<br>4：后台状态，应用位于后台。<br>5：退出状态，应用已退出。 |
| isSplitScreenMode | boolean | 是 | 判断应用是否进入分屏模式。<br>true:应用处于分屏模式。<br>false:应用不处于分屏模式。 |
| isFloatingWindowMode | boolean | 是 | 判断应用是否进入悬浮窗模式。<br>true:应用处于浮窗模式。<br>false:应用不处于浮窗模式。 |

**示例：**

ArkTS-Dyn示例：

```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let applicationStateObserver: appManager.ApplicationStateObserver = {
  onForegroundApplicationChanged(appStateData) {
    console.info(`[appManager] onForegroundApplicationChanged: ${appStateData}`);
    console.info(`appStateData.bundleName: ${appStateData.bundleName}`);
    console.info(`appStateData.uid: ${appStateData.uid}`);
    console.info(`appStateData.state: ${appStateData.state}`);
    console.info(`appStateData.isSplitScreenMode: ${appStateData.isSplitScreenMode}`);
    console.info(`appStateData.isFloatingWindowMode: ${appStateData.isFloatingWindowMode}`);
  },
  onAbilityStateChanged(abilityStateData) {
    console.info(`[appManager] onAbilityStateChanged: ${JSON.stringify(abilityStateData)}`);
  },
  onProcessCreated(processData) {
    console.info(`[appManager] onProcessCreated: ${JSON.stringify(processData)}`);
  },
  onProcessDied(processData) {
    console.info(`[appManager] onProcessDied: ${JSON.stringify(processData)}`);
  },
  onProcessStateChanged(processData) {
    console.info(`[appManager] onProcessStateChanged: ${JSON.stringify(processData)}`);
  },
  onAppStarted(appStateData) {
    console.info(`[appManager] onAppStarted: ${JSON.stringify(appStateData)}`);
  },
  onAppStopped(appStateData) {
    console.info(`[appManager] onAppStopped: ${JSON.stringify(appStateData)}`);
  }
};

try {
  const observerId = appManager.on('applicationState', applicationStateObserver);
  console.info(`[appManager] observerCode: ${observerId}`);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```

ArkTS-Sta示例：

```ts
import { appManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

class ApplicationStateObserverCustom implements appManager.ApplicationStateObserver {
  onForegroundApplicationChanged(appStateData: appManager.AppStateData) {
    console.info(`[appManager] onForegroundApplicationChanged: ${appStateData}`);
    console.info(`appStateData.bundleName: ${appStateData.bundleName}`);
    console.info(`appStateData.uid: ${appStateData.uid}`);
    console.info(`appStateData.state: ${appStateData.state}`);
    console.info(`appStateData.isSplitScreenMode: ${appStateData.isSplitScreenMode}`);
    console.info(`appStateData.isFloatingWindowMode: ${appStateData.isFloatingWindowMode}`);
  }

  onAbilityStateChanged(abilityStateData: appManager.AbilityStateData) {
    console.info(`[appManager] onAbilityStateChanged: ${JSON.stringify(abilityStateData)}`);
  }

  onProcessCreated(processData: appManager.ProcessData) {
    console.info(`[appManager] onProcessCreated: ${JSON.stringify(processData)}`);
  }

  onProcessDied(processData: appManager.ProcessData) {
    console.info(`[appManager] onProcessDied: ${JSON.stringify(processData)}`);
  }

  onProcessStateChanged(processData: appManager.ProcessData) {
    console.info(`[appManager] onProcessStateChanged: ${JSON.stringify(processData)}`);
  }

  onAppStarted(appStateData: appManager.AppStateData) {
    console.info(`[appManager] onAppStarted: ${JSON.stringify(appStateData)}`);
  }

  onAppStopped(appStateData: appManager.AppStateData) {
    console.info(`[appManager] onAppStopped: ${JSON.stringify(appStateData)}`);
  }
}

try {
  let applicationStateObserver = new ApplicationStateObserverCustom();
  const observerId = appManager.onApplicationStateChange(applicationStateObserver);
  console.info(`[appManager] observerCode: ${observerId}`);
} catch (paramError) {
  let code = (paramError as BusinessError).code;
  let message = (paramError as BusinessError).message;
  console.error(`[appManager] error: ${code}, ${message}`);
}
```