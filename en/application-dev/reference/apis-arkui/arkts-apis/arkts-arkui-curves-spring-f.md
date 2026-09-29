# spring

## Modules to Import

```TypeScript
import { curves } from '@kit.ArkUI';
```

## spring

```TypeScript
function spring(velocity: number, mass: number, stiffness: number, damping: number): string
```

Creates a spring curve. The curve shape is subject to the spring parameters, and the animation duration is subject to the **duration** parameter in **animation** and **animateTo**. Compared with [interpolatingSpring](arkts-arkui-curves-interpolatingspring-f.md), the two APIs have the same parameter signature but different behavior: **springCurve** is applicable to spring animation scenarios where the animation duration needs to be fixed. **interpolatingSpring** is applicable to physical spring animation scenarios where the animation duration is naturally determined by the spring parameters.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [springCurve](arkts-arkui-curves-springcurve-f.md)

<!--Device-curves-function spring(velocity: number, mass: number, stiffness: number, damping: number): string--><!--Device-curves-function spring(velocity: number, mass: number, stiffness: number, damping: number): string-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| velocity | number | Yes | Initial velocity. It is applied by external factors to the spring animation, designed to help ensure the smooth transition from the previous motion state. The velocity is the normalized velocity, and its value is equal to the actual velocity at the beginning of the animation divided by the animation attribute change value.<br>Value range: (-∞, +∞) |
| mass | number | Yes | Mass, which influences the inertia in the spring system. The greater the mass, the greater the amplitude of the oscillation, and the slower the speed of restoring to the equilibrium position.<br>Value range: (0, +∞) <br>**NOTE:** <br>If this parameter is set to a value less than or equal to 0, the value **1** is used. |
| stiffness | number | Yes | Stiffness. It is the degree to which an object deforms by resisting the force applied. In a spring system, the greater the stiffness, the stronger the ability to resist deformation, and the faster the speed of restoring to the equilibrium position.<br>Value range: (0, +∞) <br>**NOTE:** <br>If this parameter is set to a value less than or equal to 0, the value **1** is used. |
| damping | number | Yes | Damping. The damping coefficient in a spring system is used to describe the oscillation and attenuation of the system after being disturbed. The larger the damping, the smaller the number of oscillations of elastic motion, and the smaller the oscillation amplitude.<br>Value range: (0, +∞) <br>**NOTE:** <br>If this parameter is set to a value less than or equal to 0, the value **1** is used. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Spring curve object. |
