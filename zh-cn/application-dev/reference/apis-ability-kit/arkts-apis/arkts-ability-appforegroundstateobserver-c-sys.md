# AppForegroundStateObserver（系统接口）

定义应用启动和退出的状态监听，可以作为
[appManager.on('appForegroundState')](arkts-ability-on-f-sys.md#on-4)
的入参监听所有应用的启动和退出的变化。

**起始版本：** 11

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## onAppStateChanged

```TypeScript
onAppStateChanged(appStateData: AppStateData): void
```

应用启动和退出状态发生变化时，系统会触发该回调。

**起始版本：** 11

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appStateData | AppStateData | 是 | 应用状态信息。 |

