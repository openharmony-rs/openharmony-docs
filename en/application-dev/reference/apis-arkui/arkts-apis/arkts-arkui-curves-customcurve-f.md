# customCurve

## Modules to Import

```TypeScript
import { curves } from '@kit.ArkUI';
```

## customCurve

```TypeScript
function customCurve(interpolate: (fraction: number) => number): ICurve
```

Creates a custom curve.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| interpolate | (fraction: number) =&gt; number | Yes | Custom interpolation callback.<br>**fraction**: input x value for interpolation when the animation starts. Value range: [0, 1].<br>The return value is the y value of the curve. Value range: [0, 1].<br>**NOTE:** <br>If **fraction** is **0**, the return value **0** corresponds to the animation start point; any other return value means that the animation jumps at the start point.<br>If **fraction** is **1**, the return value **1** corresponds to the animation end point; any other return value means that the end value of the animation is not the value of the state variable, which will result in an effect of transition from that end value to the value of the state variable. |

**Return value:**

| Type | Description |
| --- | --- |
| [ICurve](arkts-arkui-curves-icurve-i.md) | Interpolation curve. |

**Examples**

```TypeScript
import { curves } from '@kit.ArkUI';
let interpolate = (fraction: number): number => {
  return Math.sqrt(fraction);
};
let curve = curves.customCurve(interpolate); // Create a custom interpolation curve.
```
