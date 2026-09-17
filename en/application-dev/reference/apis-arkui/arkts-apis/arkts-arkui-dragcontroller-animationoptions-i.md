# AnimationOptions

Defines parameters related to drag-and-drop animation effects.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { dragController } from '@kit.ArkUI';
```

## curve

```TypeScript
curve?: Curve | ICurve
```

Animation curve.

Default value: **Curve.EaseInOut**

**Type:** Curve &#124; ICurve

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## duration

```TypeScript
duration?: number
```

Animation duration, in ms.

Default value: **1000**

**NOTE:** 

- If this parameter is set to a value less than 0, the value **0** is used.  
- Floating-point values will be rounded down to integers. For example, if the value set is 1.2, **1** will be  
used.

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
