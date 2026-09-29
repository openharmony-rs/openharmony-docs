# BlanklessFrameInterpolationInfo

```TypeScript
interface BlanklessFrameInterpolationInfo
```

White-Screen-Free Loading frame interpolation status information, which is used as the callback input parameter in [BlanklessLoadingParam](arkts-arkweb-webview-blanklessloadingparam-i.md).

**Since:** 23

<!--Device-webview-interface BlanklessFrameInterpolationInfo--><!--Device-webview-interface BlanklessFrameInterpolationInfo-End-->

**System capability:** SystemCapability.Web.Webview.Core

## Modules to Import

```TypeScript
import { webview } from '@kit.ArkWeb';
```

## key

```TypeScript
key: string
```

Key value that uniquely identifies the page where the frame is interpolated. The value is the same as the key value of [setBlanklessLoadingWithParams](arkts-arkweb-webview-webviewcontroller-c.md#setblanklessloadingwithparams).

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-BlanklessFrameInterpolationInfo-key: string--><!--Device-BlanklessFrameInterpolationInfo-key: string-End-->

**System capability:** SystemCapability.Web.Webview.Core

## reason

```TypeScript
reason: string
```

Reason for the frame interpolation failure.

**Type:** string

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-BlanklessFrameInterpolationInfo-reason: string--><!--Device-BlanklessFrameInterpolationInfo-reason: string-End-->

**System capability:** SystemCapability.Web.Webview.Core

## state

```TypeScript
state: BlanklessFrameInterpolationState
```

Current frame interpolation state.

**Type:** [BlanklessFrameInterpolationState](arkts-arkweb-webview-blanklessframeinterpolationstate-e.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-BlanklessFrameInterpolationInfo-state: BlanklessFrameInterpolationState--><!--Device-BlanklessFrameInterpolationInfo-state: BlanklessFrameInterpolationState-End-->

**System capability:** SystemCapability.Web.Webview.Core

## timestamp

```TypeScript
timestamp: number
```

Time when the frame interpolation is successful, fails, or removed, in ms (UTC time).

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-BlanklessFrameInterpolationInfo-timestamp: number--><!--Device-BlanklessFrameInterpolationInfo-timestamp: number-End-->

**System capability:** SystemCapability.Web.Webview.Core
