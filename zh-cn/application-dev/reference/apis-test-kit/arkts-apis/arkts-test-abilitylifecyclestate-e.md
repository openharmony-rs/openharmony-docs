# AbilityLifecycleState

Ability生命周期状态，该类型为枚举，可配合[AbilityDelegator](application/AbilityDelegator:AbilityDelegator)的
[getAbilityState(ability)](application/AbilityDelegator:AbilityDelegator.getAbilityState)方法返回不同ability生命周期。

**起始版本：** 9

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## UNINITIALIZED

```TypeScript
UNINITIALIZED = 0
```

表示Ability处于无效状态。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## CREATE

```TypeScript
CREATE = 1
```

表示Ability处于已创建状态。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## FOREGROUND

```TypeScript
FOREGROUND = 2
```

表示Ability处于前台状态。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## BACKGROUND

```TypeScript
BACKGROUND = 3
```

表示Ability处于后台状态。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## DESTROY

```TypeScript
DESTROY = 4
```

表示Ability处于已销毁状态。

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

