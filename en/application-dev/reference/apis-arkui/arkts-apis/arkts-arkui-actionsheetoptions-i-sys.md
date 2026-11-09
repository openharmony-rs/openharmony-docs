# ActionSheetOptions (System API)

```TypeScript
interface ActionSheetOptions
```

Provides **ActionSheet** configuration options.

**Since:** 8

<!--Device-unnamed-interface ActionSheetOptions--><!--Device-unnamed-interface ActionSheetOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## distortionMode

```TypeScript
distortionMode?: DistortionMode
```

Sets the distortion animation mode of the dialog.

> **NOTE:** 
> 
> This parameter takes effect only when **systemMaterial** is set to **ImmersiveMaterial**. **DISTORTION_AUTO**
> takes effect on high- and mid-end devices and does not take effect on low-end devices. Enabling the distortion
> animation increases the rendering overhead.

**Type:** [DistortionMode](../arkts-components/arkts-arkui-common-comp-distortionmode-e-sys.md)

**Default:** DistortionMode.DISTORTION_AUTO

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ActionSheetOptions-distortionMode?: DistortionMode--><!--Device-ActionSheetOptions-distortionMode?: DistortionMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## edgeLightMode

```TypeScript
edgeLightMode?: EdgeLightMode
```

Sets the edge light animation mode of the dialog.

> **NOTE:** 
> 
> This parameter takes effect only when **systemMaterial** is set to **ImmersiveMaterial**. **EDGELIGHT_AUTO**
> takes effect on high-end devices and does not take effect on mid- or low-end devices. Enabling the edge light
> animation increases the rendering overhead.

**Type:** [EdgeLightMode](../arkts-components/arkts-arkui-common-comp-edgelightmode-e-sys.md)

**Default:** EdgeLightMode.EDGELIGHT_AUTO

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ActionSheetOptions-edgeLightMode?: EdgeLightMode--><!--Device-ActionSheetOptions-edgeLightMode?: EdgeLightMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
