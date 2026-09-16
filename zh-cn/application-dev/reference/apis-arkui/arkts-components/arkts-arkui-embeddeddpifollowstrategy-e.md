# EmbeddedDpiFollowStrategy

DPI跟随策略，用于设置DPI，使其能够跟随宿主或EmbeddedUIExtensionAbility。例如，当EmbeddedUIExtensionAbility需要与宿主应用保持视觉一致性时，可选择跟随宿主DPI；当EmbeddedUIExtensionAbility需要独立适配自身资源的DPI配置时，可选择跟随EmbeddedUIExtensionAbility DPI。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## FOLLOW_HOST_DPI

```TypeScript
FOLLOW_HOST_DPI = 0
```

表示DPI跟随宿主。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## FOLLOW_UI_EXTENSION_ABILITY_DPI

```TypeScript
FOLLOW_UI_EXTENSION_ABILITY_DPI = 1
```

表示DPI跟随EmbeddedUIExtensionAbility。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
