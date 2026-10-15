# UIExtensionOptions (System API)

```TypeScript
declare interface UIExtensionOptions
```

Used to pass optional construction parameters when the **UIExtensionComponent** is constructed.

**Since:** 11

<!--Device-unnamed-declare interface UIExtensionOptions--><!--Device-unnamed-declare interface UIExtensionOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## areaChangePlaceholder

```TypeScript
areaChangePlaceholder?: Record<string, ComponentContent>
```

Placeholder displayed when the size of **UIExtensionComponent** changes and the internal rendering of **UIExtensionAbility** is not complete. The key supports only "FOLD_TO_EXPAND" (fold-to-expand size change) and"UNDEFINED" (default size change). Other key values do not take effect. If this parameter is not set, no size-change placeholder content is displayed by default.

**Type:** Record&lt;string, ComponentContent&gt;

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

<!--Device-UIExtensionOptions-areaChangePlaceholder?: Record<string, ComponentContent>--><!--Device-UIExtensionOptions-areaChangePlaceholder?: Record<string, ComponentContent>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## dpiFollowStrategy

```TypeScript
dpiFollowStrategy?: DpiFollowStrategy
```

Provides an API for setting whether the DPI follows the host or the **UIExtensionAbility**.<br> Default value: **FOLLOW_UI_EXTENSION_ABILITY_DPI**

**Type:** [DpiFollowStrategy](arkts-arkui-uiextensioncomponent-comp-dpifollowstrategy-e-sys.md)

**Default:** DpiFollowStrategy.FOLLOW_UI_EXTENSION_ABILITY_DPI

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-UIExtensionOptions-dpiFollowStrategy?: DpiFollowStrategy--><!--Device-UIExtensionOptions-dpiFollowStrategy?: DpiFollowStrategy-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## isTransferringCaller

```TypeScript
isTransferringCaller?: boolean
```

Whether to forward the Caller information of the previous level when **UIExtensionComponent** is nested. The value **true** indicates that the Caller information of the previous level is forwarded, and **false** indicates that it is not forwarded.<br> Default value: **false**

**Type:** boolean

**Default:** false

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

<!--Device-UIExtensionOptions-isTransferringCaller?: boolean--><!--Device-UIExtensionOptions-isTransferringCaller?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## placeholder

```TypeScript
placeholder?: ComponentContent
```

Placeholder displayed before the connection between **UIExtensionComponent** and **UIExtensionAbility** is established. Pass this parameter when a loading state or prompt content needs to be displayed to users before the connection is established. If this parameter is not set, no placeholder content is displayed by default.

**Type:** ComponentContent

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-UIExtensionOptions-placeholder?: ComponentContent--><!--Device-UIExtensionOptions-placeholder?: ComponentContent-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## windowModeFollowStrategy

```TypeScript
windowModeFollowStrategy?: WindowModeFollowStrategy
```

Provides an API for setting the window mode so that it follows the host or the **UIExtensionAbility**.<br> Default value: **FOLLOW_UI_EXTENSION_ABILITY_WINDOW_MODE**

**Type:** [WindowModeFollowStrategy](arkts-arkui-uiextensioncomponent-comp-windowmodefollowstrategy-e-sys.md)

**Default:** WindowModeFollowStrategy.FOLLOW_UI_EXTENSION_ABILITY_WINDOW_MODE

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

<!--Device-UIExtensionOptions-windowModeFollowStrategy?: WindowModeFollowStrategy--><!--Device-UIExtensionOptions-windowModeFollowStrategy?: WindowModeFollowStrategy-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
