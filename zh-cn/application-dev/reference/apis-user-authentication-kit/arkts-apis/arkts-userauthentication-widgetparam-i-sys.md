# WidgetParam

用户认证界面配置相关参数。该接口用于配置认证界面的显示样式和交互方式，包括标题、导航按钮文本、窗口模式等。通过合理配置这些参数，可以为用户提供清晰的认证引导和良好的交互体验。

**起始版本：** 10

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## appWindow

```TypeScript
appWindow?: window.Window
```

是否在模应用模式下显示鉴权对话框。该模式仅适用于平板电脑和二合一设备。如果未使用此模式或使用其他类型的设备，则身份验证对话框以模系统模式显示。默认情况下，身份验证对话框以模系统方式显示。如果提供了uiContext，则该参数将
被忽略。

**类型：** window.Window

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本26.0.0开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**系统接口：** 此接口为系统接口。

## windowMode

```TypeScript
windowMode?: WindowModeType
```

用户认证界面的显示类型。用于控制系统身份认证组件的窗口样式，可选择对话框模式（DIALOG_BOX）或全屏模式（FULLSCREEN）。默认值为WindowModeType.DIALOG_BOX。

**类型：** WindowModeType

**默认值：** WindowModeType.DIALOG_BOX

**起始版本：** 10

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**系统接口：** 此接口为系统接口。

