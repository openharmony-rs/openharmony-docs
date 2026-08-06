# EmbeddedUIExtensionAbility

EmbeddedUIExtensionAbility为开发者提供了跨进程界面嵌入的能力，继承自 [UIExtensionAbility]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_。 开发者通过实现EmbeddedUIExtensionAbility，为本应用提供跨进程界面嵌入能力。例如，开发者可以在[UIAbility]\_\_\_JSDOC\_LINK\_DESC\_USD\_2\_\_\_的页面中通过 [EmbeddedComponent]\_\_\_JSDOC\_LINK\_DESC\_USD\_3\_\_\_嵌入本应用的EmbeddedUIExtensionAbility提供的界面。 各类Ability的继承关系详见\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_。 该接口在PC/2in1、Tablet中可正常调用，在其他设备类型中无法被启动。

**继承/实现关系：** EmbeddedUIExtensionAbility extends [UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md)

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export default class EmbeddedUIExtensionAbility extends UIExtensionAbility--><!--Device-unnamed-export default class EmbeddedUIExtensionAbility extends UIExtensionAbility-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

