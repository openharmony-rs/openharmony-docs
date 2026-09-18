# interpolatingSpring

## Modules to Import

```TypeScript
import { curves } from '@kit.ArkUI';
```

## interpolatingSpring

```TypeScript
function interpolatingSpring(velocity: number, mass: number, stiffness: number, damping: number): ICurve
```

Creates an interpolating spring curve animated from 0 to 1. The actual animation value is calculated based on the curve. The animation duration is subject to the curve parameters, rather than the **duration** parameter in **animation** or **animateTo**.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| velocity | number | Yes | Initial velocity. It is applied by external factors to the spring animation, designed to help ensure the smooth transition from the previous motion state. The velocity is the normalized velocity, and its value is equal to the actual velocity at the beginning of the animation divided by the animation attribute change value.<br>Value range: (-∞, +∞). |
| mass | number | Yes | Mass, which influences the inertia in the spring system. The greater the mass, the greater the amplitude of the oscillation, and the slower the speed of restoring to the equilibrium position.<br>Value range: (0, +∞). <p>**NOTE:**  <br>If this parameter is set to a value less than or equal to 0, the value **1** is used. </p> |
| stiffness | number | Yes | Stiffness. It is the degree to which an object deforms by resisting the force applied. In an elastic system, the greater the stiffness, the stronger the ability to resist deformation, and the faster the speed of restoring to the equilibrium position.<br>Value range: (0, +∞). <p>**NOTE:**  <br>If this parameter is set to a value less than or equal to 0, the value **1** is used. </p> |
| damping | number | Yes | Damping. It is used to describe the oscillation and attenuation of the system after being disturbed. The larger the damping, the smaller the number of oscillations of elastic motion, and the smaller the oscillation amplitude.<br>Value range: (0, +∞)<br> <p>**NOTE:**  <br>If this parameter is set to a value less than or equal to 0, the value **1** is used. </p> |

**Return value:**

| Type | Description |
| --- | --- |
| [ICurve](arkts-arkui-curves-icurve-i.md) | Curve. <br>Note: The spring animation curve is physics-based. Its duration depends on the **interpolatingSpring** parameters, rather than the **duration** parameter in animation, animateTo, or pageTransition. The time cannot be normalized. Therefore, the interpolation cannot be obtained using the [interpolate](arkts-arkui-curves-icurve-i.md#interpolate) function of the curve. |

**Examples**

```TypeScript
import { curves } from '@kit.ArkUI';
curves.interpolatingSpring(10, 1, 228, 30); // Create an interpolating spring curve whose duration is subject to spring parameters.
```
