# HdrDarkenBlender (System API)

HDR-adaptive darken blender, used to add a darken effect to a specified component. Before calling HdrDarkenBlender, you need to first create an HdrDarkenBlender instance through createHdrDarkenBlender.

**Since:** 26.0.0

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';
```

## grayscaleFactor

```TypeScript
grayscaleFactor?: [number, number, number]
```

Converts RGB colors to grayscale values. The weights of the grayscale conversion formula can be automatically adjusted according to the current color gamut, using different weight calculation methods under different color gamuts; suitable for sRGB and other standard color gamut scenarios. Pass this parameter when you need to customize grayscale conversion weights based on a specific color gamut or visual effect. All three components have no boundary limits. The default value is the standard grayscale weights [0.299, 0.587, 0.114].

@property { ?[double, double, double] }

**Type:** [number, number, number]

**Default:** [0.299, 0.587, 0.114]

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## hdrBrightnessRatio

```TypeScript
hdrBrightnessRatio: number
```

HDR brightness ratio. The value range is [1.0, the maximum brightness ratio supported by the current device]. Values less than 1.0 are treated as 1.0; when the value is equal to 1.0, it represents the original brightness of the component; values exceeding the maximum supported brightness ratio are treated as the maximum ratio. The maximum supported brightness ratio = device maximum brightness / device default brightness. Device maximum brightness can be obtained via hdc command: hdc shell param get const.display.brightness.max Device default brightness can be obtained via hdc command: hdc shell param get const.display.brightness.default

@property { double }

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.
