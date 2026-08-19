# OnWindowStageWillDestroyFn

```TypeScript
type OnWindowStageWillDestroyFn = (ability: UIAbility, windowStage: window.WindowStage) => void
```

注册监听应用上下文的生命周期后，在UIAbility的onWindowStageDestroy触发前回调。

**起始版本：** 23

<!--Device-unnamed-type OnWindowStageWillDestroyFn = (ability: UIAbility, windowStage: window.WindowStage) => void--><!--Device-unnamed-type OnWindowStageWillDestroyFn = (ability: UIAbility, windowStage: window.WindowStage) => void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md) | 是 | 当前Ability对象。 |
| windowStage | window.WindowStage | 是 | 当前WindowStage对象。 |

