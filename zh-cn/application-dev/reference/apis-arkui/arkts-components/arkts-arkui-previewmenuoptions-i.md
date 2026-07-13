# PreviewMenuOptions

预览菜单的选项。

**起始版本：** 18

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## hapticFeedbackMode

```TypeScript
hapticFeedbackMode? : HapticFeedbackMode
```

菜单弹出时振动效果，当ImageSpan或BuilderSpan绑定预览菜单时生效。

默认值：HapticFeedbackMode.DISABLED，菜单弹出时不振动。

**说明：** 仅当应用具备ohos.permission.VIBRATE权限，且用户启用了触感反馈时才会生效。

**类型：** HapticFeedbackMode

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

