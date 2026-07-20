# PasteButtonOptions

用于设置粘贴控件的图标、文本、按钮类型等属性。

> **说明**  
> - 建议icon或text至少传入一个。  
>  
> - 如果icon、text都不传入，PasteButton将使用默认样式创建，默认样式：PasteIconStyle默认样式为LINES；PasteDescription默认样式为PASTEButtonType默认样式为Capsule。  
>  
> - icon、text和buttonType不支持动态修改。这是因为安全控件的样式和属性在创建时已通过系统校验，动态修改可能导致控件样式不符合安全控件规范，从而影响授权的有效性。

**起始版本：** 10

<!--Device-unnamed-declare interface PasteButtonOptions--><!--Device-unnamed-declare interface PasteButtonOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## buttonType

```TypeScript
buttonType?: ButtonType
```

设置粘贴控件的按钮形状。Capsule。默认值：ButtonType。

**类型：** ButtonType

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PasteButtonOptions-buttonType?: ButtonType--><!--Device-PasteButtonOptions-buttonType?: ButtonType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: PasteIconStyle
```

设置粘贴控件的图标风格。默认值：不显示图标。<br>若同时也不传text，控件将显示为默认样式。

**类型：** PasteIconStyle

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PasteButtonOptions-icon?: PasteIconStyle--><!--Device-PasteButtonOptions-icon?: PasteIconStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
text?: PasteDescription
```

设置粘贴控件的文本描述。默认值：不显示文本描述。<br>若同时也不传icon，控件将显示为默认样式。

**类型：** PasteDescription

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-PasteButtonOptions-text?: PasteDescription--><!--Device-PasteButtonOptions-text?: PasteDescription-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

