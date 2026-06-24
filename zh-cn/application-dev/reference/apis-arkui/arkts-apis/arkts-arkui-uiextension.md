# @ohos.arkui.uiExtension

用于[EmbeddedUIExtensionAbility](../../../../application-models/embeddeduiextensionability.md)（或
[UIExtensionAbility](../../apis-ability-kit/arkts-apis/arkts-ability-uiextensionability-c.md#UIExtensionAbility)）中获取宿主应用的窗口信息或对应的
[EmbeddedComponent](./@internal/component/ets/embedded_component)<!--Del-->（或
[UIExtensionComponent](./@internal/component/ets/ui_extension_component)）<!--DelEnd-->组件的信息。

> **说明**
>
> 从API version 12开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [AvoidAreaInfo](arkts-arkui-uiextension-avoidareainfo-i.md) | 用于表示窗口避让区的信息。<br/> |
| [RectChangeOptions](arkts-arkui-uiextension-rectchangeoptions-i.md) | 组件（EmbeddedComponent或UIExtensionComponent）矩形（位置及尺寸）变化返回的值及变化原因。<br/> |
| [WindowProxy](arkts-arkui-uiextension-windowproxy-i.md) | UIExtension窗口代理。<br/> |
| <!--DelRow-->[WindowProxy](arkts-arkui-uiextension-windowproxy-i-sys.md) | UIExtension窗口代理。<br/> |
| [WindowProxyProperties](arkts-arkui-uiextension-windowproxyproperties-i.md) | 用于表示组件的相关信息。<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [EventFlag](arkts-arkui-uiextension-eventflag-e.md) | 事件类型枚举。<br/> |
| [RectChangeReason](arkts-arkui-uiextension-rectchangereason-e.md) | 组件（EmbeddedComponent或UIExtensionComponent）矩形（位置及尺寸）变化的原因。<br/> |

