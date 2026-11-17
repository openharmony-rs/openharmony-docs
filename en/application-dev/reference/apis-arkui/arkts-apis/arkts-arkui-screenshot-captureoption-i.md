# CaptureOption

```TypeScript
interface CaptureOption
```

Describes the capture options.

**Since:** 14

<!--Device-screenshot-interface CaptureOption--><!--Device-screenshot-interface CaptureOption-End-->

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## Modules to Import

```TypeScript
import { screenshot } from '@kit.ArkUI';
```

## blackWindowIds

```TypeScript
blackWindowIds?: Array<number>
```

List of window IDs that are not displayed during screen capture. By default, this list is empty. Valid window IDs must be positive integers. Currently, this parameter applies only to [floating ball windows](arkts-arkui-window-floatingball.md). If a window ID does not correspond to a floating ball window, is not a positive integer, or does not exist, error code 401 is reported. You are advised to call [getFloatingBallWindowInfo()](arkts-arkui-floatingball-floatingballcontroller-i.md#getfloatingballwindowinfo) to obtain the window ID of a floating ball window.

**Type:** Array&lt;number&gt;

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 21.

<!--Device-CaptureOption-blackWindowIds?: Array<int>--><!--Device-CaptureOption-blackWindowIds?: Array<int>-End-->

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## displayId

```TypeScript
displayId?: number
```

ID of the [display](arkts-arkui-display-displaystate-e.md) to capture. The default value is **0**. The value must be an integer greater than or equal to 0. If a non-integer is passed, error code 401 is reported.

**Type:** number

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-CaptureOption-displayId?: long--><!--Device-CaptureOption-displayId?: long-End-->

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## pixelFormat

```TypeScript
pixelFormat?: image.PixelMapFormat
```

Pixel format of the captured image. Only [RGBA_8888](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmapformat-e.md) and [BGRA_8888](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmapformat-e.md) are supported. If this parameter is not specified, the default value **image.PixelMapFormat.RGBA_8888** is used.

[

**Type:** [image.PixelMapFormat](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmapformat-e.md)

**Default:** ](https://gitcode.com/default) image.PixelMapFormat.RGBA_8888

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-CaptureOption-pixelFormat?: image.PixelMapFormat--><!--Device-CaptureOption-pixelFormat?: image.PixelMapFormat-End-->

**System capability:** SystemCapability.WindowManager.WindowManager.Core
