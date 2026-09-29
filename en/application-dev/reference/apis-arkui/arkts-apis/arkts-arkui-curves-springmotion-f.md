# springMotion

## Modules to Import

```TypeScript
import { curves } from '@kit.ArkUI';
```

## springMotion

```TypeScript
function springMotion(response?: number, dampingFraction?: number, overlapDuration?: number): ICurve
```

Creates a spring animation curve. Unlike [curves.springCurve](arkts-arkui-curves-springcurve-f.md), which uses spring physics parameters, **springMotion** uses responsive parameters to construct a curve and supports velocity inheritance between animations. It is recommended for continuous spring animations that require velocity inheritance. If multiple spring animations are applied to the same attribute of an object, each animation replaces their predecessor and inherits the velocity.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-curves-function springMotion(response?: number, dampingFraction?: number, overlapDuration?: number): ICurve--><!--Device-curves-function springMotion(response?: number, dampingFraction?: number, overlapDuration?: number): ICurve-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| response | number | No | Duration of one complete oscillation.<br>Default value: **0.55** <br>Unit: second <br>Value range: (0, +∞) <br>**NOTE:** <br>If this parameter is set to a value less than or equal to 0, the default value **0.55** is used. |
| dampingFraction | number | No | Damping coefficient.<br>**0**: undamped. In this case, the spring oscillates forever. <br>   > 0 and &lt; 1: underdamped. In this case, the spring overshoots the equilibrium position. <br>**1**: critically damped. <br> > 1: overdamped. In this case, the spring approaches equilibrium gradually. <br>Default value: **0.825** <br>Value range: [0, +∞) <br>**NOTE:** <br>A value less than 0 evaluates to the default value **0.825**. |
| overlapDuration | number | No | Duration for animations to overlap, in seconds. When animation inheritance occurs and the responses of the two spring animations are inconsistent, the response parameter smoothly transitions within the duration specified by **overlapDuration**. If **overlapDuration** is set to **0**, the response parameter does not smoothly transition but immediately switches to the new response value. <br>Default value: **0** <br>Unit: second <br>Value range: [0, +∞) <br> **NOTE:** <br>A value less than 0 evaluates to the default value **0**. <br>The spring animation curve is physics-based. Its duration depends on the **springMotion** parameters and the previous velocity, rather than the **duration** parameter in [animation](../arkts-components/arkts-arkui-common-comp.md), [animateTo](../arkts-components/arkts-arkui-common-comp.md), or [pageTransition](../arkts-components/arkts-arkui-pagetransitionenter-comp.md). The time cannot be normalized. Therefore, the interpolation cannot be obtained using the **interpolate** function of the curve. |

**Return value:**

| Type | Description |
| --- | --- |
| [ICurve](arkts-arkui-curves-icurve-i.md) | Curve. <br>**NOTE:** <br>The spring animation curve is physics-based. Its duration depends on the **springMotion** parameters and the previous velocity, rather than the **duration** parameter in [animation](../arkts-components/arkts-arkui-common-comp.md), [animateTo](../arkts-components/arkts-arkui-common-comp.md), or [pageTransition](../arkts-components/arkts-arkui-pagetransitionenter-comp.md). The time cannot be normalized. Therefore, the interpolation cannot be obtained using the [interpolate](arkts-arkui-curves-icurve-i.md#interpolate) function of the curve. |

**Examples**

```TypeScript
import { curves } from '@kit.ArkUI';
curves.springMotion(); // Create a spring animation curve with default settings.
curves.springMotion(0.5); // Create a spring animation curve with the specified response value.
curves.springMotion(0.5, 0.6); // Create a spring animation curve with the specified response and dampingFraction values.
curves.springMotion(0.5, 0.6, 0); // Create a spring animation curve with the specified parameter values.
```
