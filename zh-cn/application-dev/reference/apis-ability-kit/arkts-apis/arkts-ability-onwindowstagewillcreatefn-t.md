# OnWindowStageWillCreateFn

```TypeScript
type OnWindowStageWillCreateFn = (ability: UIAbility, windowStage: window.WindowStage) => void
```

注册监听应用上下文的生命周期后，在UIAbility的onWindowStageCreate触发前回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-type OnWindowStageWillCreateFn = (ability: UIAbility, windowStage: window.WindowStage) => void--><!--Device-unnamed-type OnWindowStageWillCreateFn = (ability: UIAbility, windowStage: window.WindowStage) => void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 当前Ability对象。  |
| windowStage | window.WindowStage | 是 | 当前WindowStage对象。  |

