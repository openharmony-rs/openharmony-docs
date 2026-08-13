# AbilityResult

定义UIAbility被拉起并退出后返回给调用方的结果码和数据。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export interface AbilityResult--><!--Device-unnamed-export interface AbilityResult-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## resultCode

```TypeScript
resultCode: int
```

目标方的UIAbility被拉起并退出后，目标方返回给拉起方的结果码。&lt;br/&gt;-?正常情况下，返回目标方传递的结果码。&lt;br/&gt;-?异常情况下，返回-1。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityResult-resultCode: int--><!--Device-AbilityResult-resultCode: int-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## want

```TypeScript
want?: Want
```

表示UIAbility被拉起并退出后返回的数据。

**类型：** [Want](arkts-ability-app-ability-want-want-c.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityResult-want?: Want--><!--Device-AbilityResult-want?: Want-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

