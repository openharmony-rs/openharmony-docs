# AbilityStageContext

AbilityStageContext是AbilityStage的上下文环境，继承自Context。 AbilityStageContext提供允许访问特定于abilityStage的资源的能力，包括获取AbilityStage对应的ModuleInfo对象、环境变化对象。

**继承/实现关系：** AbilityStageContext extends Context

**起始版本：** 23

<!--Device-unnamed-declare class AbilityStageContext--><!--Device-unnamed-declare class AbilityStageContext-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## config

```TypeScript
config: Configuration
```

环境变量。

**类型：** [Configuration](arkts-ability-app-ability-configuration-configuration-i.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityStageContext-config: Configuration--><!--Device-AbilityStageContext-config: Configuration-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## currentHapModuleInfo

```TypeScript
currentHapModuleInfo: HapModuleInfo
```

AbilityStage对应的ModuleInfo对象。

**类型：** [HapModuleInfo](arkts-ability-hapmoduleinfo-i.md)

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityStageContext-currentHapModuleInfo: HapModuleInfo--><!--Device-AbilityStageContext-currentHapModuleInfo: HapModuleInfo-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## launchElement

```TypeScript
launchElement?: ElementName
```

启动能力Stage的ElementName对象。

**类型：** [ElementName](arkts-ability-elementname-i.md)

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-AbilityStageContext-launchElement?: ElementName--><!--Device-AbilityStageContext-launchElement?: ElementName-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

