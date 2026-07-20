# SecurityUIExtensionOptions（系统接口）

该接口用于在构造时设置UIExtensionComponentAttribute的选项。

**起始版本：** 26.0.0

<!--Device-unnamed-declare interface SecurityUIExtensionOptions--><!--Device-unnamed-declare interface SecurityUIExtensionOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## dpiFollowStrategy

```TypeScript
dpiFollowStrategy?: SecurityDpiFollowStrategy
```

设置UIExtensionComponent内容的DPI跟随策略。

**类型：** SecurityDpiFollowStrategy

**默认值：** SecurityDpiFollowStrategy.FOLLOW_UI_EXTENSION_ABILITY_DPI

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SecurityUIExtensionOptions-dpiFollowStrategy?: SecurityDpiFollowStrategy--><!--Device-SecurityUIExtensionOptions-dpiFollowStrategy?: SecurityDpiFollowStrategy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## isTransferringCaller

```TypeScript
isTransferringCaller?: boolean
```

设置当前能力是否作为调用方使用。<br/>如果设置为true，作为调用方，当前UIExtensionComponent的token被设置为rootToken。

**类型：** boolean

**默认值：** false

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SecurityUIExtensionOptions-isTransferringCaller?: boolean--><!--Device-SecurityUIExtensionOptions-isTransferringCaller?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

## placeholder

```TypeScript
placeholder?: ComponentContent
```

设置占位。如果设置了占位ComponentContent，则在连接未建立时显示占位节点。

**类型：** ComponentContent

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SecurityUIExtensionOptions-placeholder?: ComponentContent--><!--Device-SecurityUIExtensionOptions-placeholder?: ComponentContent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

