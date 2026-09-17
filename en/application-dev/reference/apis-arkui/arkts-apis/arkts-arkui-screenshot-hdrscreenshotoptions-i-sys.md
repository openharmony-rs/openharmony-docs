# HdrScreenshotOptions (System API)

Describes the HDR screenshot options.

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { screenshot } from '@kit.ArkUI';
```

## displayId

```TypeScript
displayId?: number
```

ID of the [display](arkts-arkui-display-displaystate-e.md) device on which the screen region is to be captured. The value must be an integer. The default value is **0**.

**Type:** number

**Default:** The ID of the current display. The value is a positive integer greater than or equal to 0.

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.

## displayIntent

```TypeScript
displayIntent?: DisplayIntentType
```

screenshot display intent type.

**Type:** [DisplayIntentType](arkts-arkui-screenshot-displayintenttype-e-sys.md)

**Default:** DisplayIntentType.CANONICAL

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.

## isCaptureFullOfScreen

```TypeScript
isCaptureFullOfScreen?: boolean
```

Whether to capture all displays on the current screen. If the screen contains multiple displays, the value **true** means that the entire screen is captured, and **false** means that only the region of the logical screen associated with the specified display ID is captured. The default value is **false**.

**Type:** boolean

**Default:** false

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.

## isNotificationNeeded

```TypeScript
isNotificationNeeded?: boolean
```

Whether to send a notification after a snapshot is captured. **true** to send, **false** otherwise. The default value is **true**. Such a notification can be listened for through [captureStatusChange](arkts-arkui-display-on-f.md#oncapturestatuschange).

**Type:** boolean

**Default:** true

**Since:** 20

**System capability:** SystemCapability.Window.SessionManager

**System API:** This is a system API.
