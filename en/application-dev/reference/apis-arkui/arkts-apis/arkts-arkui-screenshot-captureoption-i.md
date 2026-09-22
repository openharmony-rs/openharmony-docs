# CaptureOption

```TypeScript
interface CaptureOption
```

Describes the capture options.

**Since:** 14

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

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## displayId

```TypeScript
displayId?: number
```

ID of the [display](arkts-arkui-display-displaystate-e.md) to capture. The default value is **0**. The value must be an integer greater than or equal to 0. If a non-integer is passed, error code 401 is reported.

**Type:** number

**Since:** 14

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.WindowManager.WindowManager.Core
