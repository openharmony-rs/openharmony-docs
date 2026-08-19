# AppForegroundStateObserver（系统接口）

定义应用启动和退出的状态监听，可以作为 [appManager.on('appForegroundState')](../../apis-ability-kit/arkts-apis/arkts-ability-appmanager-onapplicationstate-f.md#onapplicationstate) 的入参监听所有应用的启动和退出的变化。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-declare interface AppForegroundStateObserver--><!--Device-unnamed-declare interface AppForegroundStateObserver-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## onAppStateChanged

```TypeScript
onAppStateChanged(appStateData: AppStateData): void
```

应用启动和退出状态发生变化时，系统会触发该回调。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-AppForegroundStateObserver-onAppStateChanged(appStateData: AppStateData): void--><!--Device-AppForegroundStateObserver-onAppStateChanged(appStateData: AppStateData): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appStateData | [AppStateData](../../apis-ability-kit/arkts-apis/arkts-ability-appstatedata-c.md) | 是 | 应用状态信息。 |

