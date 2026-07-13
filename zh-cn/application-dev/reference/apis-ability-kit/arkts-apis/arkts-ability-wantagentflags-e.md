# WantAgentFlags

表示WantAgent行为控制标志，用于配置WantAgent的创建和触发行为。

**起始版本：** 9

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## ONE_TIME_FLAG

```TypeScript
ONE_TIME_FLAG = 0
```

WantAgent仅能使用一次，trigger触发后自动cancel取消。

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## NO_BUILD_FLAG

```TypeScript
NO_BUILD_FLAG
```

如果描述WantAgent对象不存在，则不创建它，直接返回null。

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## CANCEL_PRESENT_FLAG

```TypeScript
CANCEL_PRESENT_FLAG
```

在生成一个新的WantAgent对象前取消已存在的一个WantAgent对象。

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## UPDATE_PRESENT_FLAG

```TypeScript
UPDATE_PRESENT_FLAG
```

使用新的WantAgent的额外数据替换已存在的WantAgent中的额外数据。

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## CONSTANT_FLAG

```TypeScript
CONSTANT_FLAG
```

WantAgent是不可变的。

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## REPLACE_ELEMENT

```TypeScript
REPLACE_ELEMENT
```

当前Want中的element属性可被WantAgent.trigger()中Want的element属性取代。当前版本暂不支持。

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## REPLACE_ACTION

```TypeScript
REPLACE_ACTION
```

当前Want中的action属性可被WantAgent.trigger()中Want的action属性取代。当前版本暂不支持。

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## REPLACE_URI

```TypeScript
REPLACE_URI
```

当前Want中的uri属性可被WantAgent.trigger()中Want的uri属性取代。当前版本暂不支持。

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## REPLACE_ENTITIES

```TypeScript
REPLACE_ENTITIES
```

当前Want中的entities属性可被WantAgent.trigger()中Want的entities属性取代。当前版本暂不支持。

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## REPLACE_BUNDLE

```TypeScript
REPLACE_BUNDLE
```

当前Want中的bundleName属性可被WantAgent.trigger()中Want的bundleName属性取代。当前版本暂不支持。

**起始版本：** 9

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

