# OnAbilityWillSaveStateFn

```TypeScript
type OnAbilityWillSaveStateFn = (ability: UIAbility) => void
```

注册监听应用上下文的生命周期后，在UIAbility的onSaveState触发前回调。

**起始版本：** 23

<!--Device-unnamed-type OnAbilityWillSaveStateFn = (ability: UIAbility) => void--><!--Device-unnamed-type OnAbilityWillSaveStateFn = (ability: UIAbility) => void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| ability | [UIAbility](arkts-ability-app-ability-uiability-uiability-c.md) | 是 | 当前Ability对象。 |

