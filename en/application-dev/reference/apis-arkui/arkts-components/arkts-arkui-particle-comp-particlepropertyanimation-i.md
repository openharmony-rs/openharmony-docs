# ParticlePropertyAnimation

```TypeScript
interface ParticlePropertyAnimation<T>
```

Sets the lifecycle of particle properties.

**Since:** 10

<!--Device-unnamed-interface ParticlePropertyAnimation<T>--><!--Device-unnamed-interface ParticlePropertyAnimation<T>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## curve

```TypeScript
curve?: Curve | ICurve
```

Animation curve.

Default value: **Curve.Linear**

**Type:** Curve &#124; ICurve

**Default:** Curve.Linear

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ParticlePropertyAnimation-curve?: Curve | ICurve--><!--Device-ParticlePropertyAnimation-curve?: Curve | ICurve-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## endMillis

```TypeScript
endMillis: number
```

End time of the animation.

Unit: ms.

Value range: [0, +∞). If a negative value is passed in, the default value **0** is used.

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ParticlePropertyAnimation-endMillis: number--><!--Device-ParticlePropertyAnimation-endMillis: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## from

```TypeScript
from: T
```

Initial value of the property. If the value is invalid, the default value will be used.

**Type:** T

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ParticlePropertyAnimation-from: T--><!--Device-ParticlePropertyAnimation-from: T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## startMillis

```TypeScript
startMillis: number
```

Start time of the animation.

Unit: ms.

Value range: [0, +∞). If a negative value is passed in, the default value **0** is used.

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ParticlePropertyAnimation-startMillis: number--><!--Device-ParticlePropertyAnimation-startMillis: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## to

```TypeScript
to: T
```

Target value of the property. If the value is invalid, the default value will be used.

**Type:** T

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ParticlePropertyAnimation-to: T--><!--Device-ParticlePropertyAnimation-to: T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
