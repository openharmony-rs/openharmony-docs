# AbilityFirstFrameStateData（系统接口）

定义了首帧绘制完成事件回调上报的数据结构。通过[on](./../@ohos.app.ability.appManager:appManager.on(type: 'abilityFirstFrameState', observer: AbilityFirstFrameStateObserver, bundleName?: string))注册监听Ability首帧绘制完成事件后，可使用[AbilityFirstFrameStateObserver](arkts-ability-abilityfirstframestateobserver-i-sys.md)的[onAbilityFirstFrameDrawn](arkts-ability-abilityfirstframestateobserver-i-sys.md#onabilityfirstframedrawn-1)回调获取上报的数据结构。

**起始版本：** 12

<!--Device-unnamed-export interface AbilityFirstFrameStateData--><!--Device-unnamed-export interface AbilityFirstFrameStateData-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## abilityName

```TypeScript
abilityName: string
```

Ability名称。

**类型：** string

**起始版本：** 12

<!--Device-AbilityFirstFrameStateData-abilityName: string--><!--Device-AbilityFirstFrameStateData-abilityName: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## appIndex

```TypeScript
appIndex: number
```

DLP沙盒的索引。

**类型：** number

**默认值：** 0

**起始版本：** 12

<!--Device-AbilityFirstFrameStateData-appIndex: int--><!--Device-AbilityFirstFrameStateData-appIndex: int-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## bundleName

```TypeScript
bundleName: string
```

应用Bundle名称。

**类型：** string

**起始版本：** 12

<!--Device-AbilityFirstFrameStateData-bundleName: string--><!--Device-AbilityFirstFrameStateData-bundleName: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## isColdStart

```TypeScript
isColdStart: boolean
```

是否冷启动。true表示冷启动，false表示热启动。

**类型：** boolean

**默认值：** false

**起始版本：** 12

<!--Device-AbilityFirstFrameStateData-isColdStart: boolean--><!--Device-AbilityFirstFrameStateData-isColdStart: boolean-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## moduleName

```TypeScript
moduleName: string
```

应用Module名称。

**类型：** string

**起始版本：** 12

<!--Device-AbilityFirstFrameStateData-moduleName: string--><!--Device-AbilityFirstFrameStateData-moduleName: string-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

