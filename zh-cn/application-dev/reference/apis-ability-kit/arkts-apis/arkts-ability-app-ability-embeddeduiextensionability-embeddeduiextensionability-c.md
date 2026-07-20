# EmbeddedUIExtensionAbility

EmbeddedUIExtensionAbility为开发者提供了跨进程界面嵌入的能力，继承自[UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md)。开发者通过实现EmbeddedUIExtensionAbility，为本应用提供跨进程界面嵌入能力。例如，开发者可以在[UIAbility](arkts-app-ability-uiability.md)的页面中通过[EmbeddedComponent](../../apis-arkui/arkts-components/arkts-arkui-embedded_component-i)嵌入本应用的EmbeddedUIExtensionAbility提供的界面。各类Ability的继承关系详见[继承关系说明](docroot://reference/apis-ability-kit/js-apis-app-ability-ability.md#ability的继承关系说明)。该接口在PC/2in1、Tablet中可正常调用，在其他设备类型中无法被启动。

**继承/实现关系：** EmbeddedUIExtensionAbility extends [UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export default class EmbeddedUIExtensionAbility extends UIExtensionAbility--><!--Device-unnamed-export default class EmbeddedUIExtensionAbility extends UIExtensionAbility-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { EmbeddedUIExtensionAbility } from '@kit.AbilityKit';
```

