# EmbeddedOptions

```TypeScript
declare interface EmbeddedOptions
```

This interface is used to set the options for EmbeddedComponentAttribute during construction

**Since:** 26.0.0

<!--Device-unnamed-declare interface EmbeddedOptions--><!--Device-unnamed-declare interface EmbeddedOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## areaChangePlaceholder

```TypeScript
areaChangePlaceholder?: Record<string, ComponentContent>
```

Set Areachange placeholder. If the Areachange placeholder ComponentContent is set, the placeholder node is displayed until the EmbeddedComponent size change is complete.

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

Set EmbeddedComponent Content Dpi Follow Strategy.

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

Set placeholder. If set placeholder ComponentContent, show placeholder node when connection is not established.

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

Set EmbeddedComponent Content Window Mode Follow Strategy.

**Type:** [EmbeddedWindowModeFollowStrategy](arkts-arkui-embeddedcomponent-comp-embeddedwindowmodefollowstrategy-e.md)

**Default:** EmbeddedWindowModeFollowStrategy.FOLLOW_UI_EXTENSION_ABILITY_WINDOW_MODE

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-EmbeddedOptions-windowModeFollowStrategy?: EmbeddedWindowModeFollowStrategy--><!--Device-EmbeddedOptions-windowModeFollowStrategy?: EmbeddedWindowModeFollowStrategy-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
