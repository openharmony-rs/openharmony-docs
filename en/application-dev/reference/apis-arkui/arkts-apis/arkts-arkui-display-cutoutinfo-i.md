# CutoutInfo

Describes the unusable area of a display, including punch hole, notch, and curved area of a waterfall display.

**Since:** 9

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## Modules to Import

```TypeScript
import { display } from '@kit.ArkUI';
```

## boundingRects

```TypeScript
readonly boundingRects: Array<Rect>
```

Unusable areas (bounding rectangles) designed for punch holes and notches. If there are no punch holes or notches, an empty array is returned.

**Type:** Array&lt;[Rect](arkts-arkui-display-rect-i.md)&gt;

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core

## waterfallDisplayAreaRects

```TypeScript
readonly waterfallDisplayAreaRects: WaterfallDisplayAreaRects
```

Curved area on a waterfall display.

**Type:** [WaterfallDisplayAreaRects](arkts-arkui-display-waterfalldisplayarearects-i.md)

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.WindowManager.WindowManager.Core
