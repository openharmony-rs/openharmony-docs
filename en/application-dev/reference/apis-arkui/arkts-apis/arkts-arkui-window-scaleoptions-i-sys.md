# ScaleOptions (System API)

```TypeScript
interface ScaleOptions
```

Describes the scale parameters.

**Since:** 9

<!--Device-window-interface ScaleOptions--><!--Device-window-interface ScaleOptions-End-->

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## pivotX

```TypeScript
pivotX?: number
```

X coordinate of the scale center. The value is a floating-point number in the range [0.0, 1.0], and the default value is **0.5**.

**Type:** number

**Since:** 9

<!--Device-ScaleOptions-pivotX?: double--><!--Device-ScaleOptions-pivotX?: double-End-->

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

## pivotY

```TypeScript
pivotY?: number
```

Y coordinate of the scale center. The value is a floating-point number in the range [0.0, 1.0], and the default value is **0.5**.

**Type:** number

**Since:** 9

<!--Device-ScaleOptions-pivotY?: double--><!--Device-ScaleOptions-pivotY?: double-End-->

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

## x

```TypeScript
x?: number
```

Scale factor along the x-axis. The value is a floating-point number, and the default value is **1.0**.

**Type:** number

**Since:** 9

<!--Device-ScaleOptions-x?: double--><!--Device-ScaleOptions-x?: double-End-->

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.

## y

```TypeScript
y?: number
```

Scale factor along the y-axis. The value is a floating-point number, and the default value is **1.0**.

**Type:** number

**Since:** 9

<!--Device-ScaleOptions-y?: double--><!--Device-ScaleOptions-y?: double-End-->

**System capability:** SystemCapability.WindowManager.WindowManager.Core

**System API:** This is a system API.
