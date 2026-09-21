# Filter

```TypeScript
interface Filter
```

Filter effect class, used to apply corresponding effects to specified components. Before calling Filter methods, you need to first create a Filter instance through createFilter.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

## Modules to Import

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';
```

## bezierWarp

```TypeScript
bezierWarp(controlPoints: Array<common2D.Point>): Filter
```

Adds a Bezier curve deformation effect to the component. This effect achieves precise distortion and shape adjustment of the image by creating closed Bezier curves at the layer boundary. There are four Bezier curve segments, connected head to tail in sequence, with each segment containing one vertex and two tangent points. Typical application scenarios include face deformation effects, card perspective distortion, etc.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| controlPoints | Array&lt;[common2D.Point](arkts-arkgraphics2d-common2d-point-i.md)&gt; | Yes | 12 Bezier deformation control points. The array length must be 12. Changing the positions of the control points changes the shape of the curves forming the edges, thereby distorting the image. The control point coordinates use a normalized coordinate system (default range [0, 1]), and coordinate values can be greater than 1 or less than 0. If the array length is not 12, the effect will not take effect. |

**Return value:**

| Type | Description |
| --- | --- |
| [Filter](arkts-arkgraphics2d-uieffect-filter-i.md) | Returns the Filter with the Bezier curve deformation effect attached. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

```TypeScript
import { common2D, uiEffect } from '@kit.ArkGraphics2D';

@Entry
@Component
struct BezierWarpExample {
  @State valueBezier: Array<common2D.Point> = [
    { x: 0, y: 0 }, { x: 1 / 3, y: 0 }, { x: 2 / 3, y: 0 }, // top edge
    { x: 0.5, y: 0 }, { x: 0.5, y: 1 / 3 }, { x: 1, y: 2 / 3 }, // right edge
    { x: 1, y: 1 }, { x: 2 / 3, y: 1 }, { x: 1 / 3, y: 1 }, // bottom edge
    { x: 0, y: 1 }, { x: 0, y: 2 / 3 }, { x: 0, y: 1 / 3 }]; // left edge

  build() {
    Column() {
      Image($rawfile('test.jpg'))
        // Add the Bezier curve deformation effect to the component.
        .foregroundFilter(uiEffect.createFilter().bezierWarp(this.valueBezier))
    }
  }
}
```

## blurBubblesRise

```TypeScript
blurBubblesRise(param: BlurBubblesRiseEffectParam): Filter
```

Applies a blur bubbles rise effect to the image, simulating a dreamy, bubbly distortion similar to rising bubbles in liquid.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| param | [BlurBubblesRiseEffectParam](arkts-arkgraphics2d-uieffect-blurbubblesriseeffectparam-i-sys.md) | Yes | The blur bubbles rise effect parameters. |

**Return value:**

| Type | Description |
| --- | --- |
| [Filter](arkts-arkgraphics2d-uieffect-filter-i.md) | Returns the Filter with the blur bubbles rise effect attached. |

**Examples**

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';
import { image } from '@kit.ImageKit';

@Entry
@Component
struct BlurBubblesRiseExample {
  private context: Context | undefined = this.getUIContext().getHostContext();
  @State blurIntensity: number = 0.8;
  @State mixStrength: number = 0.6;
  @State progress: number = 0.5;
  @State maskImage: image.PixelMap | null = null;

  aboutToAppear() {
    if (this.context) {
      this.getImagePixelMap(this.context)
    }
  }

  getImagePixelMap(context: Context) {
    let resourceMgr = context.resourceManager;
    resourceMgr?.getMediaContent($r('app.media.drawBlurMask').id)
      .then((val: Uint8Array) => {
        let buffer: ArrayBuffer = val.buffer.slice(0, val.buffer.byteLength);
        let imageSource: image.ImageSource = image.createImageSource(buffer);
        imageSource.createPixelMap().then((pixelmap: image.PixelMap) => {
          this.maskImage = pixelmap as PixelMap;
        });
      });
  }

  build() {
    Stack() {
      Image($r('app.media.test'))
        .width('100%')
        .height('100%')
        // Apply the blur bubbles rise effect to the image, simulating the dreamy blur distortion effect of bubbles rising in liquid.
        .foregroundFilter(uiEffect.createFilter().blurBubblesRise({
          blurIntensity: this.blurIntensity,
          mixStrength: this.mixStrength,
          progress: this.progress,
          maskImage: this.maskImage
        }))
    }
    .width('100%')
    .height('100%')
  }
}
```

## colorGradient

```TypeScript
colorGradient(colors: Array<Color>, positions: Array<common2D.Point>, strengths: Array<number>,
        alphaMask?: Mask): Filter
```

Adds a color gradient effect to the component content.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| colors | Array&lt;Color&gt; | Yes | The color array for multi-color gradient. The array length range is [0, 12], and each color value must be greater than or equal to 0. If the array length is 0 or greater than 12, or if the array lengths of colors, positions, and strengths are not equal, the effect will not take effect. |
| positions | Array&lt;[common2D.Point](arkts-arkgraphics2d-common2d-point-i.md)&gt; | Yes | The position array, corresponding to the distribution positions of colors. The array length range is [0, 12]. If the array length is 0 or greater than 12, or if the array lengths of colors, positions, and strengths are not equal, the effect will not take effect. |
| strengths | Array&lt;number&gt; | Yes | The strength array, corresponding to the diffusion strength of colors. The array length range is [0, 12], and each strength value must be greater than or equal to 0. If the array length is 0 or greater than 12, or if the array lengths of colors, positions, and strengths are not equal, the effect will not take effect. |
| alphaMask | [Mask](arkts-arkgraphics2d-uieffect-mask-c-sys.md) | No | The mask that controls the transparency distribution of the gradient effect. A Mask instance can be created through Mask creation methods (such as createRippleMask, createRadialGradientMask, etc.). Pass this parameter when you need to control the transparency distribution of the color gradient effect (such as local transparency or dynamic transparency effects). If not set, the transparency of the color gradient effect is entirely determined by the colors parameter. |

**Return value:**

| Type | Description |
| --- | --- |
| [Filter](arkts-arkgraphics2d-uieffect-filter-i.md) | Returns the Filter with the color gradient effect attached. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

```TypeScript
import { common2D, uiEffect } from '@kit.ArkGraphics2D';

@Entry
@Component
struct ColorGradientExample {
  @State gradientColors: Array<uiEffect.Color> = [
    {red: 1.0, green: 0.8, blue: 0.5, alpha: 0.8},
    {red: 1.0, green: 1.5, blue: 0.5, alpha: 1.0}
  ];

  @State gradientPositions: Array<common2D.Point> = [
    {x: 0.2, y: 0.2},
    {x: 0.8, y: 0.6}
  ];

  @State gradientStrengths: Array<number> = [0.3, 0.3];

  build() {
    Column() {
      Row()
        .width('100%')
        .height('100%')
        // Add a color gradient effect to the component content.
        .backgroundFilter(uiEffect.createFilter().colorGradient(this.gradientColors, this.gradientPositions, this.gradientStrengths))
    }
  }
}
```

## contentLight

```TypeScript
contentLight(lightPosition: common2D.Point3d, lightColor: common2D.Color, lightIntensity: number,
      displacementMap?: Mask): Filter
```

Adds a 3D lighting effect to the component content.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| lightPosition | [common2D.Point3d](arkts-arkgraphics2d-common2d-point3d-i.md) | Yes | The position of the light source in the component space. [-1, -1, 0] is the top-left corner of the component, [1, 1, 0] is the bottom-right corner of the component. The larger the z-axis component, the farther the light source is from the component plane, and the larger the illuminated area. The x component range is [-10, 10], the y component range is [-10, 10], and the z component range is [0, 10]. Values outside the range will be automatically clamped. |
| lightColor | [common2D.Color](arkts-arkgraphics2d-common2d-color-i.md) | Yes | The color of the light source. The RGBA components range from [0, 1]. Values outside the range will be automatically clamped. |
| lightIntensity | number | Yes | The intensity of the light source. The value range is [0, 1]. A larger value indicates a brighter light source. Values outside the range will be automatically clamped. |
| displacementMap | [Mask](arkts-arkgraphics2d-uieffect-mask-c-sys.md) | No | The displacement map parameter. This parameter is not currently effective and is not recommended to be passed in. Not setting it has no effect on the functionality. |

**Return value:**

| Type | Description |
| --- | --- |
| [Filter](arkts-arkgraphics2d-uieffect-filter-i.md) | Returns the Filter with the content lighting effect attached. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

```TypeScript
import { common2D, uiEffect } from '@kit.ArkGraphics2D';

@Entry
@Component
struct Index {
  @State contentLightPosition: common2D.Point3d = {
    x: 0, y: 0, z: 2
  };
  @State contentLightColor: common2D.Color = {
    red: 1,
    green: 1,
    blue: 1,
    alpha: 1
  };
  @State lightIntensity: number = 1;

  build() {
    Column() {
      Stack() {
        Image($r('app.media.man'))
          .width('646px')
          .height('900px')
          .borderRadius(10)
          // Add 3D lighting effect to the component content.
          .foregroundFilter(uiEffect.createFilter().contentLight(this.contentLightPosition, this.contentLightColor, this.lightIntensity))
      }
      .width('100%')
      .height('55%')
    }
    .height('100%')
    .width('100%')
    .justifyContent(FlexAlign.Center)
    .backgroundColor('#555')
  }
}
```

## directionLight

```TypeScript
directionLight(direction: common2D.Point3d, color: Color, intensity: number, mask?: Mask, factor?: number): Filter
```

Provides a Mask-based and directional light lighting effect for the component content. Directional light illuminates the component plane from a uniform direction, with all light rays in the same direction, not attenuating with distance, and the light intensity is evenly distributed across the component, suitable for simulating distant light sources such as sunlight. Unlike the point light source of contentLight, directional light does not need to specify the specific position of the light source. Through the Mask, you can control lighting details, and through the factor, you can combine height maps to enhance the relief effect.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| direction | [common2D.Point3d](arkts-arkgraphics2d-common2d-point3d-i.md) | Yes | The direction of the incident light, represented by three-dimensional coordinates indicating the direction of the light rays. |
| color | Color | Yes | The light color. |
| intensity | number | Yes | The light intensity. The value range is [0, +∞). A larger value indicates a brighter light source. |
| mask | [Mask](arkts-arkgraphics2d-uieffect-mask-c-sys.md) | No | The displacement map, used to describe the three-dimensional details of the two-dimensional image surface. A Mask instance can be created through Mask creation methods (such as createRippleMask, createRadialGradientMask, etc.). Pass this parameter when you need to enhance local details and lighting reflection effects (such as relief, bump textures). Implemented through normal maps or height maps; if a height map is input, it needs to be used with the factor parameter. If not set, the default is empty, resulting in a global flat lighting effect without details. |
| factor | number | No | The sampling scale coefficient. Pass this parameter when using a height map as the mask and needing to control the height scaling. If not set, the mask is sampled directly as a normal map; if a value is set, the mask is sampled as a height map, and the actual height value is the product of the mask sampling value and the factor. |

**Return value:**

| Type | Description |
| --- | --- |
| [Filter](arkts-arkgraphics2d-uieffect-filter-i.md) | Returns the Filter with the lighting effect controlled by the displacement map attached. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

```TypeScript
import { uiEffect, common2D } from '@kit.ArkGraphics2D';

@Entry
@Component
struct Index {
  @State rippleMaskCenter: common2D.Point = {x:0.5, y:0.5};
  @State rippleMaskRadius: number = 0.0;
  @State rippleMaskWidth: number = 0.0;
  @State color: Color = Color.Transparent;

  build() {
    Column() {
      RelativeContainer() {
        Image($r('app.media.back')).width('100%').height('100%')
        Stack()
          .width('100%')
          .height('100%')
          .backgroundColor(this.color)
          // Provide a lighting effect based on mask and parallel light for the component content.
          .backgroundFilter(uiEffect.createFilter()
            .directionLight(
              {x:0, y:0, z:-1}, {red:2.0, green:2.0, blue:2.0, alpha:1.0}, 0.5,
              uiEffect.Mask.createRippleMask(this.rippleMaskCenter, this.rippleMaskRadius, this.rippleMaskWidth, 0.0)
              ))
          .onClick(() => {
            this.getUIContext().animateTo({duration: 1000}, () => {
              this.rippleMaskWidth = 1.0;
            })
          })
      }
    }.alignItems(HorizontalAlign.Center).borderWidth(2)
  }
}
```

## displacementDistort

```TypeScript
displacementDistort(displacementMap: Mask, factor?: [number, number]): Filter
```

Adds a distortion effect to the component content.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| displacementMap | [Mask](arkts-arkgraphics2d-uieffect-mask-c-sys.md) | Yes | The displacement map, used to control the direction and intensity of distortion. A Mask instance can be created through Mask creation methods (such as createRippleMask, createPixelMapMask, etc.). It works together with the factor to determine the degree of distortion. |
| factor | [number, number] | No | Specifies the horizontal and vertical distortion intensity coefficients. Pass this parameter when you need to control the direction and intensity of distortion (such as one-way distortion or differential distortion). The larger the absolute value of the coefficient, the more obvious the distortion. The recommended value range is [-10.0, 10.0]. If not set, the default value is [1.0, 1.0], indicating that both horizontal and vertical directions apply the default distortion intensity. Setting it to [0.0, 0.0] results in no distortion effect. The grayscale value of the Mask controls the direction and intensity of distortion, and the factor multiplied by the Mask grayscale value jointly determines the final distortion degree, i.e., actual distortion value = Mask grayscale value × factor value. |

**Return value:**

| Type | Description |
| --- | --- |
| [Filter](arkts-arkgraphics2d-uieffect-filter-i.md) | Returns the Filter with the distortion effect attached. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';

@Entry
@Component
struct DisplacementDistortExample {
  @State distortMask: uiEffect.Mask = uiEffect.Mask.createRippleMask({x: 0.5, y: 0.5}, 0.2, 0.3, 0.0);
  
  build() {
    Stack() {
      Image($rawfile('test.png'))
      Row()  
        .width('100%')
        .height('100%')
        // Add a distortion effect to the component content.
        .backgroundFilter(uiEffect.createFilter().displacementDistort(this.distortMask, [5.0, 5.0]))
    }
  }
}
```

## distort

```TypeScript
distort(distortionK: number): Filter
```

Adds a lens distortion effect to the component.

**Since:** 13

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| distortionK | number | Yes | The distortion coefficient, indicating the degree of lens distortion. The value range is [-1, 1]. Values less than -1 are treated as -1; values greater than 1 are treated as 1. When the distortion coefficient is less than 0, the effect is barrel distortion; when greater than 0, the effect is pincushion distortion. The closer the value is to 0, the smaller the distortion; when the value is 0, there is no distortion effect. |

**Return value:**

| Type | Description |
| --- | --- |
| [Filter](arkts-arkgraphics2d-uieffect-filter-i.md) | Returns the Filter with the lens distortion effect attached. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

```TypeScript
// Add the lens distortion effect to the component.
let filter = uiEffect.createFilter();
filter.distort(-0.5);
```

## edgeLight

```TypeScript
edgeLight(alpha: number, color?: Color, mask?: Mask, bloom?: boolean): Filter
```

Detects edges of the component content and adds an edge highlight effect. This effect automatically detects the edge contours of the component content and overlays a highlight stroke.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| alpha | number | Yes | Specifies the stroke highlight transparency. A larger value makes the stroke more obvious. The value range is [0, 1]. Setting it to 0 results in no stroke; values less than 0 are treated as 0; values greater than 1 are treated as 1. |
| color | Color | No | Specifies the stroke highlight color. The RGB components range from [0, +∞). Pass this parameter when you need to customize the stroke highlight color (such as emphasizing a specific color effect). If not set, the original color of the component content is used by default. When the color parameter is set, the alpha in Color does not take effect; only RGB is used. |
| mask | [Mask](arkts-arkgraphics2d-uieffect-mask-c-sys.md) | No | Specifies the stroke highlight intensity mask. A Mask instance can be created through Mask creation methods (such as createRippleMask, createRadialGradientMask, etc.). Pass this parameter when you need to control the area of the stroke highlight effect (such as local highlight instead of global highlight). If not set, the entire component content has the stroke highlight effect by default. |
| bloom | boolean | No | Specifies whether the stroke has a bloom effect. Set to true when you need to enhance the visual effect; set to false when you need a simple stroke effect. The default value is true (with bloom effect). For images smaller than 16x16, there is only a stroke effect by default, no bloom effect, and this parameter has no effect. |

**Return value:**

| Type | Description |
| --- | --- |
| [Filter](arkts-arkgraphics2d-uieffect-filter-i.md) | Returns the Filter with the edge highlight effect attached. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';

@Entry
@Component
struct EdgeLightExample {
  @State edgeLightColor: uiEffect.Color = {red: 0.0, green: 1.0, blue: 0.0, alpha: 1.0};
  
  @State edgeLightMask: uiEffect.Mask = uiEffect.Mask.createRippleMask({x: 0.5, y: 0.5}, 0.2, 0.5, 0.5);
  
  build() {
    Stack() {
      Image($rawfile('test.png'))
      Row()  
        .width('100%')
        .height('100%')
        // Detect edges for the component content and add an edge highlighting effect.
        .backgroundFilter(uiEffect.createFilter().edgeLight(1.0, this.edgeLightColor, this.edgeLightMask, false))
    }
  }
}
```

## flyInFlyOutEffect

```TypeScript
flyInFlyOutEffect(degree: number, flyMode: FlyMode): Filter
```

Adds a fly-in or fly-out deformation effect to the component. Typical application scenarios include page transition animations, window entry/exit animations, dialog pop-up animations, list item entry/exit animations, etc.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| degree | number | Yes | Indicates the degree of fly-in or fly-out deformation. The value range is [0, 1]. The closer the value is to 1, the more obvious the deformation. Values outside the range will not produce a deformation effect. |
| flyMode | [FlyMode](arkts-arkgraphics2d-uieffect-flymode-e-sys.md) | Yes | The scene mode of the fly-in or fly-out effect. BOTTOM indicates the fly-in or fly-out deformation scene from the bottom of the device. TOP indicates the fly-in or fly-out deformation scene from the top of the device. |

**Return value:**

| Type | Description |
| --- | --- |
| [Filter](arkts-arkgraphics2d-uieffect-filter-i.md) | Returns the Filter with the fly-in or fly-out deformation effect attached. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

```TypeScript
// Add the fly in/out transformation effect to the component.
let filter = uiEffect.createFilter();
filter.flyInFlyOutEffect(0.5, uiEffect.FlyMode.TOP);
```

## haloBloom

```TypeScript
haloBloom(tintColor: Color, bloomFactor: number, glowExposure: number): Filter
```

Applies a soft halo bloom effect to the image, creating a gentle glow around bright areas.

> **NOTE:** 
> 
> It is recommended to use as a foreground filter.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| tintColor | Color | Yes | Specifies the color tint applied to the halo bloom. The value is unrestricted, with a recommended range of [0, 1). The alpha channel has no effect. Values below 0 or greater than or equal to 1 have no meaningful effect. When all red, green, and blue are set to 0, no tint is applied and the halo bloom retains its original color. |
| bloomFactor | number | Yes | Controls the brightness of the halo bloom. The value is unrestricted, with a recommended range of [0, 10]. When set to 0, the halo bloom produces no visible effect. |
| glowExposure | number | Yes | Controls how far the halo bloom spreads. The value is unrestricted, with a recommended range of [0, 10]. When set to 0, the halo bloom produces no visible effect. |

**Return value:**

| Type | Description |
| --- | --- |
| [Filter](arkts-arkgraphics2d-uieffect-filter-i.md) | Returns the Filter with the halo bloom effect attached. |

## heatDistortion

```TypeScript
heatDistortion(param: HeatDistortionEffectParam): Filter
```

Applies a heat distortion effect to the image, simulating the visual distortion caused by hot air flow.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| param | [HeatDistortionEffectParam](arkts-arkgraphics2d-uieffect-heatdistortioneffectparam-i-sys.md) | Yes | The heat distortion effect parameters. |

**Return value:**

| Type | Description |
| --- | --- |
| [Filter](arkts-arkgraphics2d-uieffect-filter-i.md) | Returns the Filter with the heat distortion effect attached. |

**Examples**

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';

@Entry
@Component
struct HeatDistortionExample {
  @State intensity: number = 0.8;
  @State noiseScale: number = 2.0;
  @State riseWeight: number = 0.5;
  @State progress: number = 0.3;

  build() {
    Stack() {
      Image($r('app.media.test'))
        .width('100%')
        .height('100%')
        // Apply the heat distortion effect to the image, simulating the visual distortion caused by hot air flow.
        .foregroundFilter(uiEffect.createFilter().heatDistortion({
          intensity: this.intensity,
          noiseScale: this.noiseScale,
          riseWeight: this.riseWeight,
          progress: this.progress
        }))
    }
    .width('100%')
    .height('100%')
  }
}
```

## maskDispersion

```TypeScript
maskDispersion(dispersionMap: Mask, alpha: number, rFactor?: [number, number], gFactor?: [number, number],
      bFactor?: [number, number]): Filter
```

Adds a dispersion effect controlled by a displacement map to the component content, simulating the dispersion phenomenon when light passes through a prism. Typical application scenarios include colorful effects, prism refraction simulation, etc.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dispersionMap | [Mask](arkts-arkgraphics2d-uieffect-mask-c-sys.md) | Yes | The displacement map, used to control the intensity, direction, and transparency of dispersion. It is recommended to use a PixelMapMask-type displacement map, which allows fine-grained control over the dispersion area and intensity through custom image textures. A Mask instance can be created through the createPixelMapMask method. |
| alpha | number | Yes | The overall transparency of the dispersion effect. A smaller transparency value results in a more transparent effect. The value range is [0, 1.0]. Setting it to 0 results in no dispersion effect; values less than 0 are treated as 0; values greater than 1.0 are treated as 1.0. |
| rFactor | [number, number] | No | The basic offset of the R channel in the X/Y direction. Pass this parameter when you need to customize the dispersion intensity and direction of the red channel. A larger offset results in a more obvious red dispersion effect. If not passed, the default value is [0.0, 0.0], meaning no R channel dispersion offset. The value range for each direction is [-1.0, 1.0], and values outside the range will be automatically clamped. |
| gFactor | [number, number] | No | The basic offset of the G channel in the X/Y direction. Pass this parameter when you need to customize the dispersion intensity and direction of the green channel. If not passed, the default value is [0.0, 0.0], meaning no G channel dispersion offset. The value range is the same as rFactor, [-1.0, 1.0], and values outside the range will be automatically clamped. |
| bFactor | [number, number] | No | The basic offset of the B channel in the X/Y direction. Pass this parameter when you need to customize the dispersion intensity and direction of the blue channel. If not passed, the default value is [0.0, 0.0], meaning no B channel dispersion offset. The value range is the same as rFactor, [-1.0, 1.0], and values outside the range will be automatically clamped. |

**Return value:**

| Type | Description |
| --- | --- |
| [Filter](arkts-arkgraphics2d-uieffect-filter-i.md) | Returns the Filter with the dispersion effect controlled by the displacement map attached. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

```TypeScript
import {image} from '@kit.ImageKit';
import {common2D, uiEffect} from '@kit.ArkGraphics2D';
import {common} from '@kit.AbilityKit';

@Entry
@Component
struct MaskDispersion {
  @State pixelMap: PixelMap | null = null;
  @State src: common2D.Rect = { left: 0, top: 0, right: 1.0, bottom: 1.0 };
  @State dst: common2D.Rect = { left: 0, top: 0, right: 1.0, bottom: 1.0 };
  @State fillColor: uiEffect.Color = { red: 0, green: 0, blue: 0, alpha: 0 };

  onPageShow(): void {
    let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
    context.resourceManager.getMediaByName('mask_alpha').then(val => {
      let buffer = val.buffer.slice(0, val.buffer.byteLength);
      let imageSource = image.createImageSource(buffer);
      imageSource.createPixelMap().then(pixelMap => {
        this.pixelMap = pixelMap;
      })
    })
  }
  
  build() {
    if (this.pixelMap) {
      Stack() {
        Image($rawfile('test.png'))
        Row()  
          .width('100%')
          .height('100%')
          // Add a dispersion effect controlled by a displacement map to the component content.
          .backgroundFilter(uiEffect.createFilter().maskDispersion(
            uiEffect.Mask.createPixelMapMask(this.pixelMap!, this.src, this.dst, this.fillColor),
            1.0,
            [0.5, -0.5],
            [0.0, 0.0],
            [-0.5, 0.5]))
      }
    } else {
      Stack() {
        Image($rawfile('test.png'))
      }
    }
  }
}
```

## maskTransition

```TypeScript
maskTransition(alphaMask: Mask, factor?: number, inverse?: boolean): Filter
```

Provides a Mask-based transition effect for the component content, which can be used for page transition animations, scene transition effects, etc.

It is not recommended to use this effect during screen size changes, such as screen rotation, foldable screen opening/closing, etc.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| alphaMask | [Mask](arkts-arkgraphics2d-uieffect-mask-c-sys.md) | Yes | Specifies the area of the transition effect through a mask. A Mask instance can be created through Mask creation methods (such as createRippleMask, createRadialGradientMask, etc.). The grayscale value of the Mask determines the degree of the transition effect; a larger grayscale value results in a more obvious transition effect in that area. |
| factor | number | No | The transition coefficient. Pass this parameter when you need to control the transition progress (such as during animation or dynamic adjustment). A larger value makes the image closer to the post-transition page. If not set, the default value is 1.0 (transition completed state). The value range is [0.0, 1.0], and values outside the range will be automatically clamped to [0.0, 1.0]. |
| inverse | boolean | No | Whether to enable reverse transition. Set to true when you need a reverse transition effect (such as transitioning from the back page to the front page); set to false when you need a forward transition effect (such as transitioning from the front page to the back page). The default value is false (forward transition). |

**Return value:**

| Type | Description |
| --- | --- |
| [Filter](arkts-arkgraphics2d-uieffect-filter-i.md) | Returns the Filter with the transition effect attached. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

```TypeScript
import { uiEffect, common2D } from '@kit.ArkGraphics2D';

@Entry
@Component
struct Index {
  context = this.getUIContext();
  @State alpha: number = 0;
  @State enterNewPage:boolean = false;
  @State rippleMaskCenter: common2D.Point = {x:0.5, y:0.5};
  @State rippleMaskRadius: number = 0.1;
  build() {
    Stack() {
      // Page before the transition.
      Image($r('app.media.before')).width('100%').height('100%')
        if (this.enterNewPage) {
          // Page after the transition.
          Column().width('100%').height('100%').backgroundImage($r('app.media.after'))
            // Provide a mask-based transition effect for the component content.
            .backgroundFilter(uiEffect.createFilter()
              .maskTransition(
                uiEffect.Mask.createRadialGradientMask(this.rippleMaskCenter, this.rippleMaskRadius,this.rippleMaskRadius, [[1, 0], [1, 1]]),
                this.alpha))
            .onAppear(() => {
              this.context.animateTo({ duration: 1000 }, () => {
                this.rippleMaskRadius = 1.3;
              })
              this.context.animateTo({ duration: 800 }, () => {
                this.alpha = 1;
              })
            })
        }
    }.borderWidth(2)
    .onClick(()=>{
      this.enterNewPage = !this.enterNewPage;
      if (this.enterNewPage) {
        this.alpha = 0;
        this.rippleMaskRadius = 0.1;
      }
    })
  }
}
```

## pixelStretch

```TypeScript
pixelStretch(stretchSizes: Array<number>, tileMode: TileMode): Filter
```

Adds a pixel stretch effect to the component.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| stretchSizes | Array&lt;number&gt; | Yes | The percentage ratios of edge pixel stretching in the top, bottom, left, and right directions. The value range is [-1, 1]. A positive value indicates outward stretching, and the edge pixels of the specified original image ratio are used to fill in the top, bottom, left, and right directions. A negative value indicates inward shrinking, but the final image size remains unchanged. Note that the parameters for all four directions must be uniformly non-positive or non-negative, otherwise the effect will not take effect. |
| tileMode | TileMode | Yes | The pixel fill mode for edge pixel stretching. |

**Return value:**

| Type | Description |
| --- | --- |
| [Filter](arkts-arkgraphics2d-uieffect-filter-i.md) | Returns the Filter with the pixel stretch effect attached. |

**Examples**

```TypeScript
// Add the edge pixel extension effect to the component.
let filter = uiEffect.createFilter();
filter.pixelStretch([0.2, 0.2, 0.2, 0.2], uiEffect.TileMode.CLAMP);
```

## radiusGradientBlur

```TypeScript
radiusGradientBlur(radius: number, gradientParam: LinearGradientBlurOptions): Filter
```

Adds a radius linear gradient blur effect to the component content.

**Since:** 19

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| radius | number | Yes | Blur radius, in px. A larger blur radius results in a stronger blur effect. The value range is [0, 128]. When the blur radius is 0, there is no blur effect; values less than 0 are treated as 0; values greater than 128 are treated as 128. |
| gradientParam | LinearGradientBlurOptions | Yes | The linear gradient parameters, including fractionStops and direction. |

**Return value:**

| Type | Description |
| --- | --- |
| [Filter](arkts-arkgraphics2d-uieffect-filter-i.md) | Returns the Filter with the radius linear gradient blur effect attached. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';

@Entry
@Component
struct RadiusGradientBlurExample {
  @State blurRadiusExample: number = 64;
  @State linearGradientBlurOptionsExample: LinearGradientBlurOptions =
    {fractionStops: [[0.0, 0.0], [1.0, 1.0]], direction: GradientDirection.Bottom};

  build() {
    Column() {
      Image($rawfile('test.png'))
        // Add a radius-based linear gradient blur effect to the component content.
        .compositingFilter(uiEffect.createFilter().radiusGradientBlur(this.blurRadiusExample,
          this.linearGradientBlurOptionsExample))
    }
  }
}
```

## spinBlur

```TypeScript
spinBlur(center: common2D.Point, angle: number, samples: number): Filter
```

Applies a spin blur effect to the image, creating rotational motion trails around a specified center.

> **NOTE:** 
> 
> It is recommended to use as a foreground filter.

**Since:** 26.0.1

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| center | [common2D.Point](arkts-arkgraphics2d-common2d-point-i.md) | Yes | Specifies the blur center in normalized coordinates. [0, 0] represents the top-left corner, [0.5, 0.5] the center, and [1, 1] the bottom-right corner. |
| angle | number | Yes | Specifies the angular range of the spin blur in radians. The value is unrestricted, with a recommended range of [-2π, 2π]. Positive values rotate clockwise, while negative values rotate counterclockwise. |
| samples | number | Yes | Specifies the number of samples used for the spin blur. The value is clamped to the range [0, 128]. Higher values produce smoother results but increase processing cost; 32 is usually sufficient. |

**Return value:**

| Type | Description |
| --- | --- |
| [Filter](arkts-arkgraphics2d-uieffect-filter-i.md) | Returns the Filter with the spin blur effect attached. |

## variableRadiusBlur

```TypeScript
variableRadiusBlur(radius: number, radiusMap: Mask): Filter
```

Provides a Mask-based gradient blur effect for the component content.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| radius | number | Yes | Maximum blur radius, in px. A larger value results in a stronger blur effect. The value range is [0, 128]. When the blur radius is 0, there is no blur effect; values less than 0 are treated as 0; values greater than 128 are treated as 128. |
| radiusMap | [Mask](arkts-arkgraphics2d-uieffect-mask-c-sys.md) | Yes | The Mask object representing the degree of blurring. The grayscale value of the Mask represents the degree of blurring at the corresponding position; a larger grayscale value indicates more blurring. |

**Return value:**

| Type | Description |
| --- | --- |
| [Filter](arkts-arkgraphics2d-uieffect-filter-i.md) | Returns the Filter with the current effect attached. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';

@Entry
@Component
struct VariableRadiusBlurExample {
  @State blurMask: uiEffect.Mask = uiEffect.Mask.createRippleMask({x: 0.5, y: 0.5}, 0.2, 0.1);

  build() {
    Stack() {
      Image($rawfile('test.png'))
      Row()
        .width('100%')
        .height('100%')
        // Provide a mask-based gradient blur effect for the component content.
        .backgroundFilter(uiEffect.createFilter().variableRadiusBlur(64, this.blurMask))
    }
  }
}
```

## waterRipple

```TypeScript
waterRipple(progress: number, waveCount: number, x: number, y: number, rippleMode: WaterRippleMode): Filter
```

Adds a water ripple effect to the component.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| progress | number | Yes | Indicates the ripple progress. The value range is [0, 1]. The closer the progress is to 1, the more fully the ripples are displayed. Values outside the range will not produce a ripple effect. |
| waveCount | number | Yes | The number of waves when the water ripples. The value range is [1, 3]. The wave count must be an integer. If a floating-point number or a value outside the range is provided, the ripple effect will not appear. |
| x | number | Yes | The X-axis position of the center point where the water ripple first appears on the screen. The screen is normalized, with the top-left corner at (0, 0) and the top-right corner at (1, 0). A negative value indicates a position to the left of the screen. |
| y | number | Yes | The Y-axis position of the center point where the water ripple first appears on the screen. The screen is normalized, with the top-left corner at (0, 0) and the bottom-left corner at (0, 1). A negative value indicates a position above the screen. |
| rippleMode | [WaterRippleMode](arkts-arkgraphics2d-uieffect-waterripplemode-e-sys.md) | Yes | The scene mode of the water ripple. |

**Return value:**

| Type | Description |
| --- | --- |
| [Filter](arkts-arkgraphics2d-uieffect-filter-i.md) | Returns the Filter with the water ripple effect attached. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

```TypeScript
// Add the water ripple effect to the component.
let filter = uiEffect.createFilter();
filter.waterRipple(0.5, 2, 0.5, 0.5, uiEffect.WaterRippleMode.SMALL2SMALL);
```
