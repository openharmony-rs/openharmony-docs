# EmbeddedDpiFollowStrategy

```TypeScript
declare enum EmbeddedDpiFollowStrategy
```

Defines the DPI follow strategy, which is used to set the DPI to follow either the host or the **EmbeddedUIExtensionAbility**. For example, when the **EmbeddedUIExtensionAbility** needs to maintain visual consistency with the host app, you can choose to follow the host DPI. When the **EmbeddedUIExtensionAbility** needs to independently adapt to the DPI configuration of its own resources, you can choose to follow the **EmbeddedUIExtensionAbility** DPI.

**Since:** 26.0.0

<!--Device-unnamed-declare enum EmbeddedDpiFollowStrategy--><!--Device-unnamed-declare enum EmbeddedDpiFollowStrategy-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## FOLLOW_HOST_DPI

```TypeScript
FOLLOW_HOST_DPI = 0
```

The DPI follows the host.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EmbeddedDpiFollowStrategy-FOLLOW_HOST_DPI = 0--><!--Device-EmbeddedDpiFollowStrategy-FOLLOW_HOST_DPI = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## FOLLOW_UI_EXTENSION_ABILITY_DPI

```TypeScript
FOLLOW_UI_EXTENSION_ABILITY_DPI = 1
```

The DPI follows the **EmbeddedUIExtensionAbility**.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EmbeddedDpiFollowStrategy-FOLLOW_UI_EXTENSION_ABILITY_DPI = 1--><!--Device-EmbeddedDpiFollowStrategy-FOLLOW_UI_EXTENSION_ABILITY_DPI = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
