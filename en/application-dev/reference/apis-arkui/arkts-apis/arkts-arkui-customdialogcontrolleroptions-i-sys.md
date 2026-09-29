# CustomDialogControllerOptions

```TypeScript
declare interface CustomDialogControllerOptions
```

Defines the style of the custom dialog box.

> **NOTE:** 
> 
> - Pressing the Back or ESC key closes the dialog box.
> 
> - If the dialog box reaches its maximum allowable height on the screen when avoiding the soft keyboard, it reduces its height to fit.
> 
> It should be noted that this height adjustment is applied to the outermost container. If a child component within
> this container has been assigned a larger fixed height, since the container does not clip its content by default,
> parts of the dialog box may still be displayed off-screen.
> 
> - Use the custom dialog box to contain simple alert messages only. Do not use it as a page. When the dialog box avoids the soft keyboard, there is a 16 vp safe spacing between the two.
> 
> - For optimal visual experience, dialog box display and closing include default animations, though the animation duration may vary by device.
> 
> Note: During animation playback, the page does not respond to touch, swipe, or click interactions. To disable
> default dialog box animations, set **duration** of both **openAnimation** and **closeAnimation** to **0**.
> 
> - In ArkUI, dialog boxes do not close automatically when you switch pages unless you manually call **close**. To enable a dialog box to be dismissed during page navigation.

**Since:** 7

<!--Device-unnamed-declare interface CustomDialogControllerOptions--><!--Device-unnamed-declare interface CustomDialogControllerOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## distortionMode

```TypeScript
distortionMode?: DistortionMode
```

Sets the distortion animation Mode of the dialog.

**Type:** [DistortionMode](../arkts-components/arkts-arkui-common-comp-distortionmode-e-sys.md)

**Default:** DistortionMode.DISTORTION_AUTO

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-CustomDialogControllerOptions-distortionMode?: DistortionMode--><!--Device-CustomDialogControllerOptions-distortionMode?: DistortionMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## edgeLightMode

```TypeScript
edgeLightMode?: EdgeLightMode
```

Sets the edgeLight animation Mode of the dialog.

**Type:** [EdgeLightMode](../arkts-components/arkts-arkui-common-comp-edgelightmode-e-sys.md)

**Default:** EdgeLightMode.EDGELIGHT_AUTO

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-CustomDialogControllerOptions-edgeLightMode?: EdgeLightMode--><!--Device-CustomDialogControllerOptions-edgeLightMode?: EdgeLightMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
