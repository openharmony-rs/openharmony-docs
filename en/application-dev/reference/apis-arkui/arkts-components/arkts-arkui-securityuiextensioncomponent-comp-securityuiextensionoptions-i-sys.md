# SecurityUIExtensionOptions (System API)

```TypeScript
declare interface SecurityUIExtensionOptions
```

Defines the options to be passed when constructing **SecurityUIExtensionComponent**.

**Since:** 26.0.0

<!--Device-unnamed-declare interface SecurityUIExtensionOptions--><!--Device-unnamed-declare interface SecurityUIExtensionOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## dpiFollowStrategy

```TypeScript
dpiFollowStrategy?: SecurityDpiFollowStrategy
```

Resolution following strategy for **SecurityUIExtensionComponent**, used to control whether the embedded **UIExtensionAbility** content follows the host application's resolution or uses its own resolution. Default value: **FOLLOW_UI_EXTENSION_ABILITY_DPI**.

**Type:** [SecurityDpiFollowStrategy](arkts-arkui-securityuiextensioncomponent-comp-securitydpifollowstrategy-e-sys.md)

**Default:** SecurityDpiFollowStrategy.FOLLOW_UI_EXTENSION_ABILITY_DPI

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SecurityUIExtensionOptions-dpiFollowStrategy?: SecurityDpiFollowStrategy--><!--Device-SecurityUIExtensionOptions-dpiFollowStrategy?: SecurityDpiFollowStrategy-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## isTransferringCaller

```TypeScript
isTransferringCaller?: boolean
```

Whether the **UIExtensionComponent** forwards the upper-level caller information when it is used for nesting. **true**: yes; **false**: no. The default value is **false**.

**Type:** boolean

**Default:** false

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SecurityUIExtensionOptions-isTransferringCaller?: boolean--><!--Device-SecurityUIExtensionOptions-isTransferringCaller?: boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## placeholder

```TypeScript
placeholder?: ComponentContent
```

Placeholder to be displayed before the **SecurityUIExtensionComponent** establishes a connection with the **UIExtensionAbility**.

**Type:** ComponentContent

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SecurityUIExtensionOptions-placeholder?: ComponentContent--><!--Device-SecurityUIExtensionOptions-placeholder?: ComponentContent-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
