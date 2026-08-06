# PreloadedUIExtensionAbilityLoadedFn（系统接口）

```TypeScript
export type PreloadedUIExtensionAbilityLoadedFn = (preloadId: int) => void
```

预加载[UIExtensionAbility]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_被加载时的回调函数类型。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-abilityManager-export type PreloadedUIExtensionAbilityLoadedFn = (preloadId: int) => void--><!--Device-abilityManager-export type PreloadedUIExtensionAbilityLoadedFn = (preloadId: int) => void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.AbilityCore

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| preloadId | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | The preload UIExtensionAbility ID.  |

