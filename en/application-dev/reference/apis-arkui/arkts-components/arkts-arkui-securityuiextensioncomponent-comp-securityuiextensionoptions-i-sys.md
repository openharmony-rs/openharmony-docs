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

Resolution following strategy for **SecurityUIExtensionComponent**, used to control whether the embedded **UIExtensionAbility** content follows the host application's resolution or uses its own resolution.<br>Default value: **FOLLOW_UI_EXTENSION_ABILITY_DPI**

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

Whether to forward the Caller information of the upper-level caller (that is, the identity information of the **Ability** that initiates the call) when **SecurityUIExtensionComponent** is nested, so as to support call chain passing in multi-level nesting scenarios.<br>**true**: forwards the Caller information of the upper level; **false**: does not forward the Caller information of the upper level.<br>Default value: **false**

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

Placeholder displayed before the connection between **SecurityUIExtensionComponent** and the **UIExtensionAbility** is established. No placeholder is displayed if this attribute is not set.

**Type:** ComponentContent

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SecurityUIExtensionOptions-placeholder?: ComponentContent--><!--Device-SecurityUIExtensionOptions-placeholder?: ComponentContent-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
