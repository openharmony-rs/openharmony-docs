# BlurOptions

Grayscale blur parameters.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## grayscale

```TypeScript
grayscale: [number, number]
```

Grayscale blur, with two parameters in the value range of [0, 127]. The color gradation of the black and white in the image is adjusted to create different shades of gray. The first parameter indicates the brightness of the black color, and the second parameter indicates the darkness of the white color. A larger value indicates a more obvious adjustment effect (the black and white colors become grayer). The valid value range is 0–127. For example, if the value specified is (20,20), the RGB value [0, 0, 0] (black) is converted to [20, 20, 20], RGB value [255, 255, 255] (white) is converted to [235, 235, 235] (255-20), and the color pixels remain unchanged.

**Type:** [number, number]

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
