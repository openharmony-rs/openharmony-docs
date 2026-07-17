# WantAgentFlags

表示WantAgent行为控制标志，用于配置WantAgent的创建和触发行为。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** WantAgentFlags

<!--Device-wantAgent-export enum WantAgentFlags--><!--Device-wantAgent-export enum WantAgentFlags-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## ONE_TIME_FLAG

```TypeScript
ONE_TIME_FLAG = 0
```

WantAgent仅能使用一次。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** ONE_TIME_FLAG

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WantAgentFlags-ONE_TIME_FLAG = 0--><!--Device-WantAgentFlags-ONE_TIME_FLAG = 0-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## NO_BUILD_FLAG

```TypeScript
NO_BUILD_FLAG
```

如果描述WantAgent对象不存在，则不创建它，直接返回null。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** NO_BUILD_FLAG

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WantAgentFlags-NO_BUILD_FLAG--><!--Device-WantAgentFlags-NO_BUILD_FLAG-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## CANCEL_PRESENT_FLAG

```TypeScript
CANCEL_PRESENT_FLAG
```

在生成一个新的WantAgent对象前取消已存在的一个WantAgent对象。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** CANCEL_PRESENT_FLAG

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WantAgentFlags-CANCEL_PRESENT_FLAG--><!--Device-WantAgentFlags-CANCEL_PRESENT_FLAG-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## UPDATE_PRESENT_FLAG

```TypeScript
UPDATE_PRESENT_FLAG
```

使用新的WantAgent的额外数据替换已存在的WantAgent中的额外数据。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** UPDATE_PRESENT_FLAG

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WantAgentFlags-UPDATE_PRESENT_FLAG--><!--Device-WantAgentFlags-UPDATE_PRESENT_FLAG-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## CONSTANT_FLAG

```TypeScript
CONSTANT_FLAG
```

WantAgent是不可变的。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** CONSTANT_FLAG

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WantAgentFlags-CONSTANT_FLAG--><!--Device-WantAgentFlags-CONSTANT_FLAG-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## REPLACE_ELEMENT

```TypeScript
REPLACE_ELEMENT
```

当前Want中的element属性可被WantAgent.trigger()中Want的element属性取代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** REPLACE_ELEMENT

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WantAgentFlags-REPLACE_ELEMENT--><!--Device-WantAgentFlags-REPLACE_ELEMENT-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## REPLACE_ACTION

```TypeScript
REPLACE_ACTION
```

当前Want中的action属性可被WantAgent.trigger()中Want的action属性取代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** REPLACE_ACTION

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WantAgentFlags-REPLACE_ACTION--><!--Device-WantAgentFlags-REPLACE_ACTION-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## REPLACE_URI

```TypeScript
REPLACE_URI
```

当前Want中的uri属性可被WantAgent.trigger()中Want的uri属性取代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** REPLACE_URI

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WantAgentFlags-REPLACE_URI--><!--Device-WantAgentFlags-REPLACE_URI-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## REPLACE_ENTITIES

```TypeScript
REPLACE_ENTITIES
```

当前Want中的entities属性可被WantAgent.trigger()中Want的entities属性取代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** REPLACE_ENTITIES

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WantAgentFlags-REPLACE_ENTITIES--><!--Device-WantAgentFlags-REPLACE_ENTITIES-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## REPLACE_BUNDLE

```TypeScript
REPLACE_BUNDLE
```

当前Want中的bundleName属性可被WantAgent.trigger()中Want的bundleName属性取代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** REPLACE_BUNDLE

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-WantAgentFlags-REPLACE_BUNDLE--><!--Device-WantAgentFlags-REPLACE_BUNDLE-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

