# PreloadedUIExtensionAbilityDestroyedFn（系统接口）

```TypeScript
export type PreloadedUIExtensionAbilityDestroyedFn = (preloadId: number) => void
```

预加载[UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md)被销毁时的回调函数类型。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-abilityManager-export type PreloadedUIExtensionAbilityDestroyedFn = (preloadId: int) => void--><!--Device-abilityManager-export type PreloadedUIExtensionAbilityDestroyedFn = (preloadId: int) => void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| preloadId | number | 是 | The preload UIExtensionAbility ID.  |

