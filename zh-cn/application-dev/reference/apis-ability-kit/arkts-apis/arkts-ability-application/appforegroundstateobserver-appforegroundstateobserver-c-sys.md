# AppForegroundStateObserver（系统接口）

定义应用启动和退出的状态监听，可以作为 [appManager.on('appForegroundState')]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ 的入参监听所有应用的启动和退出的变化。

**起始版本：** 11

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为11。

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

<!--Device-AppForegroundStateObserver-onAppStateChanged(appStateData: AppStateData): void--><!--Device-AppForegroundStateObserver-onAppStateChanged(appStateData: AppStateData): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appStateData | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 应用状态信息。 |

