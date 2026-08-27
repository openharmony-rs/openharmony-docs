# ExtensionContext

ExtensionContext是[ExtensionAbility](arkts-ability-app-ability-extensionability-extensionability-c.md)的上下文环境，继承自 [Context](../../../reference/apis-ability-kit/js-apis-inner-application-context.md#context)。 ExtensionContext模块提供访问特定[ExtensionAbility](arkts-ability-app-ability-extensionability-extensionability-c.md)的资源的能力。

**继承/实现关系：** ExtensionContext extends Context

**起始版本：** 9

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## config

```TypeScript
config: Configuration
```

当前ExtensionAbility的配置信息，可用于获取语言、颜色模式等配置。

**类型：** [Configuration](arkts-ability-app-ability-configuration-configuration-i.md)

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## currentHapModuleInfo

```TypeScript
currentHapModuleInfo: HapModuleInfo
```

当前ExtensionAbility所属HAP模块的信息，包含模块名称、类型、描述等。

**类型：** [HapModuleInfo](arkts-ability-hapmoduleinfo-i.md)

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## extensionAbilityInfo

```TypeScript
extensionAbilityInfo: ExtensionAbilityInfo
```

当前[ExtensionAbility](arkts-ability-app-ability-extensionability-extensionability-c.md)的信息，包含名称、类型、标签ID等。

**类型：** [ExtensionAbilityInfo](arkts-ability-extensionabilityinfo-i.md)

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core
