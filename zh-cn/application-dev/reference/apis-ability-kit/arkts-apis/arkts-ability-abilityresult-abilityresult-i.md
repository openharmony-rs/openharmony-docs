# AbilityResult

定义UIAbility被拉起并退出后返回给调用方的结果码和数据。

**起始版本：** 7

<!--Device-unnamed-export interface AbilityResult--><!--Device-unnamed-export interface AbilityResult-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## resultCode

```TypeScript
resultCode: number
```

目标方的UIAbility被拉起并退出后，目标方返回给拉起方的结果码。<br/>-?正常情况下，返回目标方传递的结果码。<br/>-?异常情况下，返回-1。

**类型：** number

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityResult-resultCode: int--><!--Device-AbilityResult-resultCode: int-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

## want

```TypeScript
want?: Want
```

表示UIAbility被拉起并退出后返回的数据。

**类型：** Want

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityResult-want?: Want--><!--Device-AbilityResult-want?: Want-End-->

**系统能力：** SystemCapability.Ability.AbilityBase

