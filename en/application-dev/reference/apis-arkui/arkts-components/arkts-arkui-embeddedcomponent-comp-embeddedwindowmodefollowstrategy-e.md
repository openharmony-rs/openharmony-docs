# EmbeddedWindowModeFollowStrategy

```TypeScript
declare enum EmbeddedWindowModeFollowStrategy
```

Defines the window mode follow strategy, which is used to set the window mode to follow either the host or the **EmbeddedUIExtensionAbility**. For example, when the **EmbeddedUIExtensionAbility** needs to maintain the same window mode (such as full screen or split screen) as the host app, you can choose to follow the host. When the **EmbeddedUIExtensionAbility** needs to independently control the window mode, you can choose to follow the **EmbeddedUIExtensionAbility**.

**Since:** 26.0.0

<!--Device-unnamed-declare enum EmbeddedWindowModeFollowStrategy--><!--Device-unnamed-declare enum EmbeddedWindowModeFollowStrategy-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## FOLLOW_HOST_WINDOW_MODE

```TypeScript
FOLLOW_HOST_WINDOW_MODE = 0
```

The window mode follows the host.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EmbeddedWindowModeFollowStrategy-FOLLOW_HOST_WINDOW_MODE = 0--><!--Device-EmbeddedWindowModeFollowStrategy-FOLLOW_HOST_WINDOW_MODE = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## FOLLOW_UI_EXTENSION_ABILITY_WINDOW_MODE

```TypeScript
FOLLOW_UI_EXTENSION_ABILITY_WINDOW_MODE = 1
```

The window mode follows the **EmbeddedUIExtensionAbility**.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EmbeddedWindowModeFollowStrategy-FOLLOW_UI_EXTENSION_ABILITY_WINDOW_MODE = 1--><!--Device-EmbeddedWindowModeFollowStrategy-FOLLOW_UI_EXTENSION_ABILITY_WINDOW_MODE = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
