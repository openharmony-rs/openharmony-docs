# @ohos.arkui.uiExtension

用于[EmbeddedUIExtensionAbility](docroot://application-models/embeddeduiextensionability.md)（或[UIExtensionAbility](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-uiextensionability-uiextensionability-c.md)）中获取宿主应用的窗口信息或对应的[EmbeddedComponent](../../apis-arkui/arkts-components/arkts-arkui-embedded_component-i)<!--Del-->（或[UIExtensionComponent](../../apis-arkui/arkts-components/arkts-arkui-ui_extension_component-i)）<!--DelEnd-->组件的信息。

> **说明**  
>  
> 从API version 12开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。

**起始版本：** 12

<!--Device-unnamed-declare namespace uiExtension--><!--Device-unnamed-declare namespace uiExtension-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { uiExtension } from '@kit.ArkUI';
```

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [AvoidAreaInfo](arkts-arkui-uiextension-avoidareainfo-i.md) | 用于表示窗口避让区的信息。 |
| [RectChangeOptions](arkts-arkui-uiextension-rectchangeoptions-i.md) | 组件（EmbeddedComponent或UIExtensionComponent）矩形（位置及尺寸）变化返回的值及变化原因。 |
| [WindowProxy](arkts-arkui-uiextension-windowproxy-i.md) | UIExtension窗口代理。 |
| [WindowProxyProperties](arkts-arkui-uiextension-windowproxyproperties-i.md) | 用于表示组件的相关信息。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [WindowProxy](arkts-arkui-uiextension-windowproxy-i-sys.md) | UIExtension窗口代理。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [EventFlag](arkts-arkui-uiextension-eventflag-e.md) | 事件类型枚举。 |
| [RectChangeReason](arkts-arkui-uiextension-rectchangereason-e.md) | 组件（EmbeddedComponent或UIExtensionComponent）矩形（位置及尺寸）变化的原因。 |

