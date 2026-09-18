# ScreenshotOptions (System API)

Describes the screenshot options.

**Since:** 7

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { screenshot } from '@kit.ArkUI';
```

## displayId

```TypeScript
displayId?: number
```

ID of the [display](arkts-arkui-display-displaystate-e.md) device on which the screen region is to be captured. The value must be an integer.

**Type:** number

**Since:** 8

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

## imageSize

```TypeScript
imageSize?: Size
```

Region of the screen to capture. If no value is passed, the region of the logical screen associated with the specified display ID is returned.

**Type:** Size

**Since:** 7

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

## isCaptureFullOfScreen

```TypeScript
isCaptureFullOfScreen?: boolean
```

Whether to capture all displays on the current screen. If the screen contains multiple displays, the value **true** means that the entire screen is captured, and **false** means that only the region of the logical screen associated with the specified display ID is captured.

**Type:** boolean

**Since:** 20

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

## isNotificationNeeded

```TypeScript
isNotificationNeeded?: boolean
```

Whether to send a notification after a snapshot is captured. **true** to send, **false** otherwise. The default value is **true**. Such a notification can be listened for through [captureStatusChange](arkts-arkui-display-on-f.md#oncapturestatuschange).

**Type:** boolean

**Since:** 14

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

## rotation

```TypeScript
rotation?: number
```

Angle by which the captured image should be rotated. Currently, the value can be **0** only. The default value is **0**.

**Type:** number

**Since:** 7

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

## screenRect

```TypeScript
screenRect?: Rect
```

Region of the screen to capture. If no value is passed, the region of the logical screen associated with the specified display ID is returned.

**Type:** [Rect](arkts-arkui-screenshot-rect-i.md)

**Since:** 7

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.
