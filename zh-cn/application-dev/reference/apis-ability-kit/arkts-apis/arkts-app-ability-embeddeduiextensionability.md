# @ohos.app.ability.EmbeddedUIExtensionAbility

## 导入模块

```TypeScript
import { EmbeddedUIExtensionAbility } from '@kit.AbilityKit';
```

## 汇总

### 类

| 名称 | 说明 |
| --- | --- |
| [EmbeddedUIExtensionAbility](arkts-ability-app-ability-embeddeduiextensionability-embeddeduiextensionability-c.md) | EmbeddedUIExtensionAbility为开发者提供了跨进程界面嵌入的能力，继承自[UIExtensionAbility](arkts-ability-app-ability-uiextensionability-uiextensionability-c.md)。开发者通过实现EmbeddedUIExtensionAbility，为本应用提供跨进程界面嵌入能力。例如，开发者可以在[UIAbility](arkts-app-ability-uiability.md)的页面中通过[EmbeddedComponent](../../apis-arkui/arkts-components/arkts-arkui-embedded_component-i)嵌入本应用的EmbeddedUIExtensionAbility提供的界面。各类Ability的继承关系详见[继承关系说明](docroot://reference/apis-ability-kit/js-apis-app-ability-ability.md#ability的继承关系说明)。该接口在PC/2in1、Tablet中可正常调用，在其他设备类型中无法被启动。 |

