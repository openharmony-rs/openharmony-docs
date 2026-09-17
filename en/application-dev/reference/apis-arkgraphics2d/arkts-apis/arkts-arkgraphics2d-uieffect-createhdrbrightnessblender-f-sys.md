# createHdrBrightnessBlender (System API)

## Modules to Import

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';
```

## createHdrBrightnessBlender

```TypeScript
function createHdrBrightnessBlender(param: BrightnessBlenderParam): HdrBrightnessBlender
```

Creates an HdrBrightnessBlender instance for adding an HDR-enabled brightness effect to a component.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| param | [BrightnessBlenderParam](arkts-arkgraphics2d-graphics-uieffect-brightnessblenderparam-i-sys.md) | Yes | The brightness blender parameters, including grayscale adjustment coefficients, saturation, blending ratio, and other configuration items, used to configure the brightness effect. |

**Return value:**

| Type | Description |
| --- | --- |
| [HdrBrightnessBlender](arkts-arkgraphics2d-uieffect-hdrbrightnessblender-i-sys.md) | Returns the HDR-enabled brightness blender. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';

// Create a BrightnessBlender instance that supports HDR.
let blender: uiEffect.HdrBrightnessBlender =
  uiEffect.createHdrBrightnessBlender({cubicRate:1.0, quadraticRate:1.0, linearRate:1.0, degree:1.0, saturation:1.0,
    positiveCoefficient:[2.3, 4.5, 2.0], negativeCoefficient:[0.5, 2.0, 0.5], fraction:0.0});

@Entry
@Component
struct Example {
  build() {
    RelativeContainer() {
      Image($r('app.media.screenshot'))
        .width('100%')
        .height('100%')
        .advancedBlendMode(blender)
    }
  }
}
```
