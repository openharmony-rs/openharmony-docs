# ForegroundBlur

```TypeScript
export interface ForegroundBlur
```

Sets the foreground blur effect. The blur radius can be used to control the blur degree.

**Since:** 26.0.0

<!--Device-unnamed-export interface ForegroundBlur--><!--Device-unnamed-export interface ForegroundBlur-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## radius

```TypeScript
radius: number
```

Blur radius.

Unit: px

Value range: [0, +∞). Default value: **0**. A negative value, **NaN**, and **Infinity** are invalid and treated as the default value. A larger value indicates a more obvious background blur effect. If the value is **0**, the background is not blurred.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ForegroundBlur-radius: double--><!--Device-ForegroundBlur-radius: double-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
