# AbilityForegroundStateObserver（系统接口）

定义应用前后台状态监听。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare interface AbilityForegroundStateObserver--><!--Device-unnamed-declare interface AbilityForegroundStateObserver-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

## onAbilityStateChanged

```TypeScript
onAbilityStateChanged(abilityStateData: AbilityStateData): void
```

当Ability前后台状态发生变化时，系统会触发该回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-AbilityForegroundStateObserver-onAbilityStateChanged(abilityStateData: AbilityStateData): void--><!--Device-AbilityForegroundStateObserver-onAbilityStateChanged(abilityStateData: AbilityStateData): void-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| abilityStateData | [AbilityStateData](../../apis-ability-kit/arkts-apis/arkts-ability-abilitystatedata-c.md) | 是 | Ability状态信息。 |

