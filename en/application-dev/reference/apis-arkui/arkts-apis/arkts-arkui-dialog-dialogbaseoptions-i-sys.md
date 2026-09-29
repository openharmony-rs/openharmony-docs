# DialogBaseOptions

```TypeScript
declare interface DialogBaseOptions
```

Base options shared by all dialog types.

**Since:** 26.0.1

<!--Device-dialog-declare interface DialogBaseOptions--><!--Device-dialog-declare interface DialogBaseOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { dialog, DialogBaseAlignment, DialogButtonOrientation, DialogState, DialogResult, DialogDismissal, DialogBaseController } from '@kit.ArkUI';
```

## distortionMode

```TypeScript
distortionMode?: DistortionMode
```

Nonlinear animation mode of the dialog box under the system material. Default value: DistortionMode.DISTORTION_AUTO.

**Type:** [DistortionMode](../arkts-components/arkts-arkui-common-comp-distortionmode-e-sys.md)

**Default:** DistortionMode.DISTORTION_AUTO

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-DialogBaseOptions-distortionMode?: DistortionMode--><!--Device-DialogBaseOptions-distortionMode?: DistortionMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## edgeLightMode

```TypeScript
edgeLightMode?: EdgeLightMode
```

Edge light animation mode of the dialog box under the system material. Default value: EdgeLightMode.EDGELIGHT_AUTO.

**Type:** [EdgeLightMode](../arkts-components/arkts-arkui-common-comp-edgelightmode-e-sys.md)

**Default:** EdgeLightMode.EDGELIGHT_AUTO

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

<!--Device-DialogBaseOptions-edgeLightMode?: EdgeLightMode--><!--Device-DialogBaseOptions-edgeLightMode?: EdgeLightMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
