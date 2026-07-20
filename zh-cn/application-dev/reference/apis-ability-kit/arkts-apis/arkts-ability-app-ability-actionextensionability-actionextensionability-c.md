# ActionExtensionAbility

ActionExtensionAbility是为开发者提供的自定义操作业务模板，继承自[UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md)。

开发者通过实现ActionExtensionAbility，为其他应用提供内容查看与处理功能。例如，开发者使用ActionExtensionAbility实现了文本翻译功能。其他应用可以通过调用该ActionExtensionAbility来处理需要翻译的内容，并获取到处理后的翻译内容。

各类Ability的继承关系详见[继承关系说明](docroot://reference/apis-ability-kit/js-apis-app-ability-ability.md#ability的继承关系说明)。

**继承/实现关系：** ActionExtensionAbility extends [UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md)

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export default class ActionExtensionAbility extends UIExtensionAbility--><!--Device-unnamed-export default class ActionExtensionAbility extends UIExtensionAbility-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { ActionExtensionAbility } from '@kit.AbilityKit';
```

