# WidgetParam

用户认证界面配置相关参数。该接口用于配置认证界面的显示样式和交互方式，包括标题、导航按钮文本、窗口模式等。通过合理配置这些参数，可以为用户提供清晰的认证引导和良好的交互体验。

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-userAuth-interface WidgetParam--><!--Device-userAuth-interface WidgetParam-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

## appWindow

```TypeScript
appWindow?: window.Window
```

应用窗口对象。用于以模应用弹窗方式显示身份认证对话框，适用于需要通过窗口对象控制认证对话框显示的场景。如果已提供此参数，则uiContext将被忽略。

**类型：** window.Window

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-WidgetParam-appWindow?: window.Window--><!--Device-WidgetParam-appWindow?: window.Window-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**系统接口：** 此接口为系统接口。

## windowMode

```TypeScript
windowMode?: WindowModeType
```

用户认证界面的显示类型。DIALOG\_BOX适用于大多数认证场景（用户体验较好），FULLSCREEN适用于需要沉浸式认证体验或认证信息较多的场景。不传入时默认为WindowModeType.DIALOG\_BOX。

**类型：** WindowModeType

**默认值：** WindowModeType.DIALOG_BOX

**起始版本：** 10

**ArkTS模式：** ArkTS-Dyn起始版本为10；ArkTS-Sta起始版本为23。

<!--Device-WidgetParam-windowMode?: WindowModeType--><!--Device-WidgetParam-windowMode?: WindowModeType-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**系统接口：** 此接口为系统接口。

