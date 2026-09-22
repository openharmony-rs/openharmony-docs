# UIExtensionOptions (System API)

```TypeScript
declare interface UIExtensionOptions
```

Describes the optional construction parameters during **UIExtensionComponent** construction.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## areaChangePlaceholder

```TypeScript
areaChangePlaceholder?: Record<string, ComponentContent>
```

Placeholder for size changes, displayed when the UIExtensionComponent's size changes and the internal rendering of **UIExtension** is not completed. The key value can be **FOLD_TO_EXPAND** (size change for folding and expanding) or **UNDEFINED** (default size change).

**Type:** Record&lt;string, ComponentContent&gt;

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## dpiFollowStrategy

```TypeScript
dpiFollowStrategy?: DpiFollowStrategy
```

Whether the DPI settings follow the host or UIExtensionAbility.

Default value: **FOLLOW_UI_EXTENSION_ABILITY_DPI**

**Type:** [DpiFollowStrategy](arkts-arkui-uiextensioncomponent-comp-dpifollowstrategy-e-sys.md)

**Default:** DpiFollowStrategy.FOLLOW_UI_EXTENSION_ABILITY_DPI

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## isTransferringCaller

```TypeScript
isTransferringCaller?: boolean
```

Whether the **UIExtensionComponent** forwards the upper-level caller information when it is used for nesting.

Default value: **false**

**Type:** boolean

**Default:** false

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## placeholder

```TypeScript
placeholder?: ComponentContent
```

Placeholder to be displayed before the UIExtensionComponent establishes a connection with the UIExtensionAbility.

**Type:** ComponentContent

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## windowModeFollowStrategy

```TypeScript
windowModeFollowStrategy?: WindowModeFollowStrategy
```

Following strategy of the window mode.

Default value: **FOLLOW_UI_EXTENSION_ABILITY_WINDOW_MODE**

**Type:** [WindowModeFollowStrategy](arkts-arkui-uiextensioncomponent-comp-windowmodefollowstrategy-e-sys.md)

**Default:** WindowModeFollowStrategy.FOLLOW_UI_EXTENSION_ABILITY_WINDOW_MODE

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
