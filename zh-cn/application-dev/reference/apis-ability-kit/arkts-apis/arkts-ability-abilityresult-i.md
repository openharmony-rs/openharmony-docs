# AbilityResult

定义UIAbility被拉起并退出后返回给调用方的结果码和数据。

**起始版本：** 7

**系统能力：** SystemCapability.Ability.AbilityBase

## resultCode

```TypeScript
resultCode: number
```

目标方的UIAbility被拉起并退出后，目标方返回给拉起方的结果码。<br/>-?正常情况下，返回目标方传递的结果码。<br/>-?异常情况下，返回-1。

**类型：** number

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityBase

## want

```TypeScript
want?: Want
```

表示UIAbility被拉起并退出后返回的数据。

**类型：** Want

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityBase

