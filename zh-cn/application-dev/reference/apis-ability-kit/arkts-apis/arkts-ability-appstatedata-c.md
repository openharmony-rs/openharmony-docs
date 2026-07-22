# AppStateData

定义应用状态信息，使用接口[on](@ohos.app.ability.appManager:appManager.on(type: 'applicationState', observer: ApplicationStateObserver))注册应用状态变化监听后，当应用、进程或组件的状态变化时，系统通过[ApplicationStateObserver](arkts-ability-applicationstateobserver-c.md)的[onForegroundApplicationChanged](../../../reference/apis-ability-kit/js-apis-inner-application-applicationStateObserver.md#applicationstateobserveronforegroundapplicationchanged)等方法回调给开发者。

**起始版本：** 14

<!--Device-unnamed-declare class AppStateData--><!--Device-unnamed-declare class AppStateData-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## bundleName

```TypeScript
bundleName: string
```

Bundle名称。

**类型：** string

**起始版本：** 14

<!--Device-AppStateData-bundleName: string--><!--Device-AppStateData-bundleName: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## isFloatingWindowMode

```TypeScript
isFloatingWindowMode: boolean
```

判断应用是否处于悬浮窗模式。

true:应用处于悬浮窗模式。

false:应用不处于悬浮窗模式。

**类型：** boolean

**起始版本：** 14

<!--Device-AppStateData-isFloatingWindowMode: boolean--><!--Device-AppStateData-isFloatingWindowMode: boolean-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## isSplitScreenMode

```TypeScript
isSplitScreenMode: boolean
```

判断应用是否处于分屏模式。

true:应用处于分屏模式。

false:应用不处于分屏模式。

**类型：** boolean

**起始版本：** 14

<!--Device-AppStateData-isSplitScreenMode: boolean--><!--Device-AppStateData-isSplitScreenMode: boolean-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## state

```TypeScript
state: number
```

应用状态。

0：初始化状态，应用正在初始化

1：就绪状态，应用已初始化完毕

2：前台状态，应用位于前台

3：获焦状态。（预留状态，当前暂不支持）

4：后台状态，应用位于后台

5：退出状态，应用已退出

**类型：** number

**起始版本：** 14

<!--Device-AppStateData-state: int--><!--Device-AppStateData-state: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## uid

```TypeScript
uid: number
```

应用程序的uid。

**类型：** number

**起始版本：** 14

<!--Device-AppStateData-uid: int--><!--Device-AppStateData-uid: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

