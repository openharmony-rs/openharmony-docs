# springCurve

## Modules to Import

```TypeScript
import { curves } from '@kit.ArkUI';
```

## springCurve

```TypeScript
function springCurve(velocity: number, mass: number, stiffness: number, damping: number): ICurve
```

Creates a spring curve. The curve shape is subject to the spring parameters, and the animation duration is subject to the **duration** parameter in **animation** and **animateTo**.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| velocity | number | Yes | Initial velocity. It is applied by external factors to the spring animation, designed to help ensure the smooth transition from the previous motion state. The velocity is the normalized velocity, and its value is equal to the actual velocity at the beginning of the animation divided by the animation attribute change value.Value range: (-∞, +∞). |
| mass | number | Yes | Mass, which influences the inertia in the spring system. The greater the mass, the greater the amplitude of the oscillation, and the slower the speed of restoring to the equilibrium position. Value range: (0, +∞). <p>**NOTE:**<br>If this parameter is set to a value less than or equal to 0, the value 1 is used. </p> |
| stiffness | number | Yes | Stiffness.It is the degree to which an object deforms by resisting the force applied. In an elastic system, the greater the stiffness, the stronger the ability to resist deformation, and the faster the speed of restoring to the equilibrium position.Value range: (0, +∞). <p>**NOTE:**<br>If this parameter is set to a value less than or equal to 0, the value 1 is used. </p> |
| damping | number | Yes | Damping. It is used to describe the oscillation and attenuation of the system after being disturbed. The larger the damping, the smaller the number of oscillations of elastic motion, and the smaller the oscillation amplitude.Value range: (0, +∞). <p>**NOTE:**<br>If this parameter is set to a value less than or equal to 0, the value 1 is used. </p> |

**Return value:**

| Type | Description |
| --- | --- |
| [ICurve](arkts-arkui-curves-icurve-i.md) | Interpolation curve. |

**Examples**

```TypeScript
import { curves } from '@kit.ArkUI';
curves.springCurve(10, 1, 228, 30); // Create a spring curve.
```
