# SaveButtonOptions

用于设置保存控件的图标、文本、按钮类型等属性。
> **说明**  
>  
> - 建议icon或text至少传入一个。  
>  
> - 如果icon、text都不传入，SaveButton将使用默认样式创建，默认样式：SaveIconStyle默认样式为FULL_FILLED；  
> SaveDescription默认样式为DOWNLOAD；ButtonType默认样式为Capsule。  
>  
> - icon、text和buttonType不支持动态修改。

**起始版本：** 10

<!--Device-unnamed-declare interface SaveButtonOptions--><!--Device-unnamed-declare interface SaveButtonOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## buttonType

```TypeScript
buttonType?: ButtonType
```

设置保存控件的背景样式。默认值：ButtonType.Capsule。

**类型：** ButtonType

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SaveButtonOptions-buttonType?: ButtonType--><!--Device-SaveButtonOptions-buttonType?: ButtonType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## icon

```TypeScript
icon?: SaveIconStyle
```

设置保存控件的图标风格。<br>不传入该参数表示不显示图标；若同时也不传text，整体配置将显示为默认样式。

**类型：** SaveIconStyle

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SaveButtonOptions-icon?: SaveIconStyle--><!--Device-SaveButtonOptions-icon?: SaveIconStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## text

```TypeScript
text?: SaveDescription
```

设置保存控件的文本描述。<br>不传入该参数表示不显示文本描述；若同时也不传icon，整体配置将显示为默认样式。

**类型：** SaveDescription

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SaveButtonOptions-text?: SaveDescription--><!--Device-SaveButtonOptions-text?: SaveDescription-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

