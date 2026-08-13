# EmbeddedUIExtensionAbility

EmbeddedUIExtensionAbility为开发者提供了跨进程界面嵌入的能力，继承自 [UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md#UIExtensionAbility)。 开发者通过实现EmbeddedUIExtensionAbility，为本应用提供跨进程界面嵌入能力。例如，开发者可以在[UIAbility](arkts-ability-app-ability-uiability-uiability-c.md#UIAbility)的页面中通过 EmbeddedComponent嵌入本应用的EmbeddedUIExtensionAbility提供的界面。 各类Ability的继承关系详见继承关系说明。 该接口在PC/2in1、Tablet中可正常调用，在其他设备类型中无法被启动。

**继承/实现关系：** EmbeddedUIExtensionAbility extends [UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md#UIExtensionAbility)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export default class EmbeddedUIExtensionAbility--><!--Device-unnamed-export default class EmbeddedUIExtensionAbility-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

