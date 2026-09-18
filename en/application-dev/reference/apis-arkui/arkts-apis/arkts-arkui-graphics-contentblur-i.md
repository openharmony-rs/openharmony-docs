# ContentBlur

Sets a content blur effect.

**Since:** 26.0.0

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## grayscale

```TypeScript
grayscale?: [number, number]
```

Grayscale blur, with two parameters in the value range of [0, 127]. The default value is [0, 0]. The color gradation of the black and white in the image is adjusted to create different shades of gray. The first parameter indicates the degree of brightening the black color, and the second parameter indicates the degree of darkening the white color. A larger value indicates a more obvious adjustment (black and white become more gray). For example, if the value specified is (20, 20), the RGB value [0, 0, 0] (black) is adjusted to [20, 20, 20] (0+20), RGB value [255, 255, 255] (white) is adjusted to [235, 235, 235] (255-20), and the color pixels remain unchanged in the image.

**Type:** [number, number]

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## radius

```TypeScript
radius: number
```

Blur radius. The value range is [0, +∞). The default value is **0**. A negative value, **NaN**, and **Infinity** are invalid and treated as the default value. A larger value indicates a more obvious blur effect. If the value is **0**, the content is not blurred.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
