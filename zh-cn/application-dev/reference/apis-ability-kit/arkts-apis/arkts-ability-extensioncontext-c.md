# ExtensionContext

ExtensionContext是[ExtensionAbility](arkts-ability-app-ability-extensionability-extensionability-c.md)的上下文环境，继承自[Context](../../../../reference/apis-ability-kit/js-apis-inner-application-context.md#context)。ExtensionContext模块提供访问特定[ExtensionAbility](arkts-ability-app-ability-extensionability-extensionability-c.md)的资源的能力。

**继承/实现关系：** ExtensionContext extends [Context](arkts-ability-context-t.md)

**起始版本：** 9

<!--Device-unnamed-declare class ExtensionContext extends Context--><!--Device-unnamed-declare class ExtensionContext extends Context-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## config

```TypeScript
config: Configuration
```

所属Module的配置信息。

**类型：** Configuration

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ExtensionContext-config: Configuration--><!--Device-ExtensionContext-config: Configuration-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## currentHapModuleInfo

```TypeScript
currentHapModuleInfo: HapModuleInfo
```

所属Hap包的信息。

**类型：** HapModuleInfo

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ExtensionContext-currentHapModuleInfo: HapModuleInfo--><!--Device-ExtensionContext-currentHapModuleInfo: HapModuleInfo-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## extensionAbilityInfo

```TypeScript
extensionAbilityInfo: ExtensionAbilityInfo
```

所属[ExtensionAbility](arkts-ability-app-ability-extensionability-extensionability-c.md)的信息。

**类型：** ExtensionAbilityInfo

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ExtensionContext-extensionAbilityInfo: ExtensionAbilityInfo--><!--Device-ExtensionContext-extensionAbilityInfo: ExtensionAbilityInfo-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

