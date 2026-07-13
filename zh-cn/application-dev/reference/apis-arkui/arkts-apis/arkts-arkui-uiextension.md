# @ohos.arkui.uiExtension

用于[EmbeddedUIExtensionAbility](../../../../application-models/embeddeduiextensionability.md)（或
[UIExtensionAbility](../../apis-ability-kit/arkts-apis/arkts-ability-uiextensionability-c.md)）中获取宿主应用的窗口信息或对应的
[EmbeddedComponent](./@internal/component/ets/embedded_component)<!--Del-->（或
[UIExtensionComponent](./@internal/component/ets/ui_extension_component)）<!--DelEnd-->组件的信息。

> **说明**
>
> 从API version 12开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [AvoidAreaInfo](arkts-arkui-avoidareainfo-i.md) | 用于表示窗口避让区的信息。 |
| [RectChangeOptions](arkts-arkui-rectchangeoptions-i.md) | 组件（EmbeddedComponent或UIExtensionComponent）矩形（位置及尺寸）变化返回的值及变化原因。 |
| [WindowProxy](arkts-arkui-windowproxy-i.md) | UIExtension窗口代理。 |
| [WindowProxyProperties](arkts-arkui-windowproxyproperties-i.md) | 用于表示组件的相关信息。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [WindowProxy](arkts-arkui-windowproxy-i-sys.md) | UIExtension窗口代理。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [EventFlag](arkts-arkui-eventflag-e.md) | 事件类型枚举。 |
| [RectChangeReason](arkts-arkui-rectchangereason-e.md) | 组件（EmbeddedComponent或UIExtensionComponent）矩形（位置及尺寸）变化的原因。 |

