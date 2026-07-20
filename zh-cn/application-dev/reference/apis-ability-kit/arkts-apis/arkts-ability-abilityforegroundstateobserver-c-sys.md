# AbilityForegroundStateObserver（系统接口）

定义应用前后台状态监听。

**起始版本：** 11

<!--Device-unnamed-export default class AbilityForegroundStateObserver--><!--Device-unnamed-export default class AbilityForegroundStateObserver-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

<a id="onabilitystatechanged"></a>
## onAbilityStateChanged

```TypeScript
onAbilityStateChanged(abilityStateData: AbilityStateData): void
```

当Ability前后台状态发生变化时，系统会触发该回调。

**起始版本：** 11

<!--Device-AbilityForegroundStateObserver-onAbilityStateChanged(abilityStateData: AbilityStateData): void--><!--Device-AbilityForegroundStateObserver-onAbilityStateChanged(abilityStateData: AbilityStateData): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| abilityStateData | [AbilityStateData](arkts-ability-abilitystatedata-c.md) | 是 | Ability状态信息。 |

