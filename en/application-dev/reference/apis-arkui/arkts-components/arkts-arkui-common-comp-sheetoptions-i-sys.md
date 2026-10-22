# SheetOptions (System API)

```TypeScript
declare interface SheetOptions extends BindOptions
```

Optional attributes of the sheet. Inherits from [BindOptions](arkts-arkui-common-comp-bindoptions-i.md).

**Inheritance/Implementation:** SheetOptions extends [BindOptions](arkts-arkui-common-comp-bindoptions-i.md)

**Since:** 10

<!--Device-unnamed-declare interface SheetOptions extends BindOptions--><!--Device-unnamed-declare interface SheetOptions extends BindOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## blurSnapshot

```TypeScript
blurSnapshot?: BlurSnapshotOptions
```

Blur snapshot optimization option of the sheet popup, used to reduce the computational overhead of blur rendering. When a significant increase in power consumption is observed while using **blurStyle** or **systemMaterial** to set the blur or material effect, you can enable blur optimization. After it is enabled, if the sheet popup is configured with **blurStyle** or **systemMaterial**, its blur effect is rendered using snapshots to reduce computational overhead; if **blurStyle** or **systemMaterial** is not set, enabling **enableBlurSnapshot** does not produce a blur optimization effect. This attribute does not support dynamic switching between a value and undefined after the sheet popup is displayed. If you attempt to switch it after the popup is displayed, the setting does not take effect. The POPUP type of the sheet popup does not support blur optimization. If **enableBlurSnapshot** is set to true on the POPUP type, the setting does not take effect.

Default value: undefined, which disables blur optimization

**Type:** [BlurSnapshotOptions](arkts-arkui-common-comp-blursnapshotoptions-i-sys.md)

**Default:** undefined

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SheetOptions-blurSnapshot?: BlurSnapshotOptions--><!--Device-SheetOptions-blurSnapshot?: BlurSnapshotOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## closeButtonMaterial

```TypeScript
closeButtonMaterial?: SystemUiMaterial
```

System material effect of the close button. Default value: **undefined**, indicating that no material is set.

**Type:** [SystemUiMaterial](arkts-arkui-common-comp-systemuimaterial-t.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-SheetOptions-closeButtonMaterial?: SystemUiMaterial--><!--Device-SheetOptions-closeButtonMaterial?: SystemUiMaterial-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## edgeLightMode

```TypeScript
edgeLightMode?: EdgeLightMode
```

Sets the edge light effect animation mode of the sheet popup. The edge light flow animation takes effect only when [SheetType](arkts-arkui-common-comp-sheettype-e.md) is BOTTOM. When this attribute is not set, the edge light effect animation is disabled by default. For the edge light effect animation of the sheet popup, EDGELIGHT_AUTO: disabled on all computing devices; EDGELIGHT_ENABLED: enables the edge light effect animation; EDGELIGHT_DISABLED: disables the edge light effect animation.

Default value: EdgeLightMode.EDGELIGHT_DISABLED

**Type:** [EdgeLightMode](arkts-arkui-common-comp-edgelightmode-e-sys.md)

**Default:** EdgeLightMode.EDGELIGHT_DISABLED

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SheetOptions-edgeLightMode?: EdgeLightMode--><!--Device-SheetOptions-edgeLightMode?: EdgeLightMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## offset

```TypeScript
offset?: Position
```

Sets the offset of the sheet popup. The bottom spacing can be set only when the sheet popup is a bottom popup. The **detents** attribute in [SheetOptions](arkts-arkui-common-comp-sheetoptions-i.md) of the sheet popup is not supported. When the y-axis is set to a positive number, the setting does not take effect and falls back to the default value 0vp.

Default value: the x-axis coordinate is 0vp, and the y-axis coordinate is 0vp.

**Type:** Position

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

<!--Device-SheetOptions-offset?: Position--><!--Device-SheetOptions-offset?: Position-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## titleBarBackgroundBlur

```TypeScript
titleBarBackgroundBlur?: SheetTitleBarBackgroundBlurOptions
```

Background blur effect of the title bar. Supports customizing blur parameters via options.

**Type:** [SheetTitleBarBackgroundBlurOptions](arkts-arkui-common-comp-sheettitlebarbackgroundbluroptions-i-sys.md)

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-SheetOptions-titleBarBackgroundBlur?: SheetTitleBarBackgroundBlurOptions--><!--Device-SheetOptions-titleBarBackgroundBlur?: SheetTitleBarBackgroundBlurOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
