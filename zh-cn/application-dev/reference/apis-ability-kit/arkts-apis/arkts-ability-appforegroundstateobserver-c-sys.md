# AppForegroundStateObserver（系统接口）

定义应用启动和退出的状态监听，可以作为 [appManager.on('appForegroundState')](arkts-ability-appmanager-onapplicationstate-f.md#on_applicationState) 的入参监听所有应用的启动和退出的变化。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

<!--Device-unnamed-export default class AppForegroundStateObserver--><!--Device-unnamed-export default class AppForegroundStateObserver-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## onAppStateChanged

```TypeScript
onAppStateChanged(appStateData: AppStateData): void
```

应用启动和退出状态发生变化时，系统会触发该回调。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

**废弃版本：** -1

<!--Device-AppForegroundStateObserver-onAppStateChanged(appStateData: AppStateData): void--><!--Device-AppForegroundStateObserver-onAppStateChanged(appStateData: AppStateData): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appStateData | [AppStateData](arkts-ability-appstatedata-c.md) | 是 | 应用状态信息。 |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { appManager } from '@kit.AbilityKit';

let observer: appManager.AppForegroundStateObserver = {
  onAppStateChanged(appStateData: appManager.AppStateData) {
    console.info(`onAppStateChanged appStateData: ${JSON.stringify(appStateData)}`);
  },
};
appManager.on('appForegroundState', observer);
```

ArkTS-Sta示例：

```TypeScript
'use static'
import { appManager } from '@kit.AbilityKit';

class MyObserver implements appManager.AppForegroundStateObserver {
  onAppStateChanged(appStateData: appManager.AppStateData) {
    console.info(`onAppStateChanged appStateData: ${JSON.stringify(appStateData)}`);
  }
}

let observer = new MyObserver();
appManager.onAppForegroundStateChange(observer);
```

