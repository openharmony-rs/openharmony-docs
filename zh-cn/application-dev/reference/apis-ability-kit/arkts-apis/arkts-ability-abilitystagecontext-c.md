# AbilityStageContext

AbilityStageContext是AbilityStage的上下文环境，继承自[Context](arkts-ability-context-depr-i.md)。
AbilityStageContext提供允许访问特定于abilityStage的资源的能力，包括获取AbilityStage对应的ModuleInfo对象、环境变化对象。

**继承/实现关系：** AbilityStageContext extends [Context](arkts-ability-context-t.md)

**起始版本：** 9

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## config

```TypeScript
config: Configuration
```

环境变量。

**类型：** Configuration

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## currentHapModuleInfo

```TypeScript
currentHapModuleInfo: HapModuleInfo
```

AbilityStage对应的ModuleInfo对象。

**类型：** HapModuleInfo

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## launchElement

```TypeScript
launchElement?: ElementName
```

启动能力Stage的ElementName对象。

**类型：** ElementName

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本24开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

