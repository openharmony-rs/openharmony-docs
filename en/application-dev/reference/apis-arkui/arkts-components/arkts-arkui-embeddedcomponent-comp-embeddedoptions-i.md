# EmbeddedOptions

```TypeScript
declare interface EmbeddedOptions
```

Used to pass optional construction parameters when creating an **EmbeddedComponent**.

**Since:** 26.0.0

<!--Device-unnamed-declare interface EmbeddedOptions--><!--Device-unnamed-declare interface EmbeddedOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## areaChangePlaceholder

```TypeScript
areaChangePlaceholder?: Record<string, ComponentContent>
```

Sets the size-change placeholder, which is displayed when the size of the **EmbeddedComponent** changes and the content rendering of the **EmbeddedUIExtensionAbility** is not complete. The key is the size-change scenario type (for example, **"FOLD_TO_EXPAND"** indicates the fold-to-expand scenario), and the value is the placeholder component for the corresponding scenario. The currently supported key includes: **FOLD_TO_EXPAND**. If an unsupported key is passed in, the placeholder does not take effect. Default value: **null**, indicating that no size-change placeholder is set.

**Type:** Record&lt;string, ComponentContent&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EmbeddedOptions-areaChangePlaceholder?: Record<string, ComponentContent>--><!--Device-EmbeddedOptions-areaChangePlaceholder?: Record<string, ComponentContent>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## dpiFollowStrategy

```TypeScript
dpiFollowStrategy?: EmbeddedDpiFollowStrategy
```

DPI to follow the host or the **EmbeddedUIExtensionAbility**.<br>Default value: **FOLLOW_UI_EXTENSION_ABILITY_DPI**, indicating that the DPI follows the **EmbeddedUIExtensionAbility**.

**Type:** [EmbeddedDpiFollowStrategy](arkts-arkui-embeddedcomponent-comp-embeddeddpifollowstrategy-e.md)

**Default:** EmbeddedDpiFollowStrategy.FOLLOW_UI_EXTENSION_ABILITY_DPI

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EmbeddedOptions-dpiFollowStrategy?: EmbeddedDpiFollowStrategy--><!--Device-EmbeddedOptions-dpiFollowStrategy?: EmbeddedDpiFollowStrategy-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## placeholder

```TypeScript
placeholder?: ComponentContent
```

Placeholder to display before the **EmbeddedComponent** establishes a connection with the **EmbeddedUIExtensionAbility**.<br>Default value: **null**, indicating no placeholder is displayed.

**Type:** ComponentContent

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EmbeddedOptions-placeholder?: ComponentContent--><!--Device-EmbeddedOptions-placeholder?: ComponentContent-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## windowModeFollowStrategy

```TypeScript
windowModeFollowStrategy?: EmbeddedWindowModeFollowStrategy
```

Window mode to follow the host or the **EmbeddedUIExtensionAbility**.<br>Default value: **FOLLOW_UI_EXTENSION_ABILITY_WINDOW_MODE**, indicating that the window mode follows the **EmbeddedUIExtensionAbility**.<br>**Since:** 26.0.0

**Type:** [EmbeddedWindowModeFollowStrategy](arkts-arkui-embeddedcomponent-comp-embeddedwindowmodefollowstrategy-e.md)

**Default:** EmbeddedWindowModeFollowStrategy.FOLLOW_UI_EXTENSION_ABILITY_WINDOW_MODE

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EmbeddedOptions-windowModeFollowStrategy?: EmbeddedWindowModeFollowStrategy--><!--Device-EmbeddedOptions-windowModeFollowStrategy?: EmbeddedWindowModeFollowStrategy-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
