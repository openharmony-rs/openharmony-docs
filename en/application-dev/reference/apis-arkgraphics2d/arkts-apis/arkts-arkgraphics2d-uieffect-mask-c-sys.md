# Mask (System API)

Mask effect class, used as input for Filter and VisualEffect. Different types of Mask provide different grayscale distribution patterns, such as wave ring masks, radial gradients, pixel map masks, etc.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';
```

## createBinocularMask

```TypeScript
static createBinocularMask(radiusX: number, radiusY: number, gap: number, softness: number): Mask
```

Creates a binocular mask. Generates a left‑right symmetric dual‑elliptical‑arc mask shape, which is used together with the maskDispersion filter to control the area and direction of the dispersion effect.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| radiusX | number | Yes | Semi‑major axis of the binocular ellipses. Value range: [0, 1.0]; out‑of‑range values will be clamped internally. |
| radiusY | number | Yes | Semi‑minor axis of the binocular ellipses. Value range: [0, 1.0]; out‑of‑range values will be clamped internally. |
| gap | number | Yes | Horizontal offset of each ellipse center from origin. Value range: [0, 1.0]; out‑of‑range values will be clamped internally. |
| softness | number | Yes | Edge softness of the binocular mask shape. Value range: [0, 1.0]; out‑of‑range values will be clamped internally. |

**Return value:**

| Type | Description |
| --- | --- |
| [Mask](arkts-arkgraphics2d-uieffect-mask-c-sys.md) | Mask instance carrying the binocular mask effect. |

## createFractalGlassMask

```TypeScript
static createFractalGlassMask(glassNum: number, glassStrength: number, glassSoftness: number,
      isSymmetric: boolean, refractMask?: image.PixelMap): Mask
```

Creates a fractal glass mask. It performs periodic horizontal displacement sampling on the input texture via fractal stripes to produce a glass‑refraction‑like distortion effect. Distortion can be made symmetric around the image vertical axis. Combined with displacementDistort, it produces a grating refraction visual effect.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| glassNum | number | Yes | Number of fractal glass stripes. Value range: [0, 100]; out‑of‑range values will be clamped internally. |
| glassStrength | number | Yes | Distortion strength of the fractal glass. Value range: [0, 10]; out‑of‑range values will be clamped internally. |
| glassSoftness | number | Yes | Edge softness of fractal glass stripes. Value range: [0, 0.01]; out‑of‑range values will be clamped internally. |
| isSymmetric | boolean | Yes | Whether to enable symmetric distortion."Symmetric" refers to centering around the vertical axis of the image. |
| refractMask | [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) | No | PixelMap instance created by the image module. Optional parameter to control the effective region of the fractal effect. If provided, glassNum no longer denotes stripe quantity. GlassNum and glassStrength jointly determine refraction intensity. |

**Return value:**

| Type | Description |
| --- | --- |
| [Mask](arkts-arkgraphics2d-uieffect-mask-c-sys.md) | Mask instance carrying the fractal‑glass mask effect. |

## createPixelMapMask

```TypeScript
static createPixelMapMask(pixelMap: image.PixelMap, srcRect: common2D.Rect, dstRect: common2D.Rect,
      fillColor?: Color): Mask
```

Creates a Mask instance with scaling effect by inputting a pixelMap, the area of the pixelMap to be drawn, the drawing area of the mounted node, and the color to fill outside the drawing area.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pixelMap | [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) | Yes | The PixelMap instance created by the image module. It can be obtained through image decoding or direct creation. |
| srcRect | [common2D.Rect](arkts-arkgraphics2d-common2d-rect-i.md) | Yes | The area of the pixelMap to be drawn. The leftmost and topmost positions correspond to 0, and the rightmost and bottommost positions correspond to 1. right must be greater than left, and bottom must be greater than top; otherwise the effect will not take effect. |
| dstRect | [common2D.Rect](arkts-arkgraphics2d-common2d-rect-i.md) | Yes | The drawing area of the pixelMap on the node where the mask is mounted. The leftmost and topmost positions of the node correspond to 0, and the rightmost and bottommost positions correspond to 1. right must be greater than left, and bottom must be greater than top; otherwise the effect will not take effect. |
| fillColor | Color | No | The color to fill the area outside the pixelMap drawing area on the node. Each component range is [0, 1], default is transparent color. Values less than 0 are treated as 0, and values greater than 1 are treated as 1. |

**Return value:**

| Type | Description |
| --- | --- |
| [Mask](arkts-arkgraphics2d-uieffect-mask-c-sys.md) | Returns a Mask instance created based on the pixelMap. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

```TypeScript
import { image } from '@kit.ImageKit';
import { uiEffect, common2D } from '@kit.ArkGraphics2D';
import { BusinessError } from '@kit.BasicServicesKit';

const colorBuffer = new ArrayBuffer(96);
let opts: image.InitializationOptions = {
  editable: true,
  pixelFormat: 3,
  size: {
    height: 4,
    width: 6
  }
};
image.createPixelMap(colorBuffer, opts).then((pixelMap) => {
  let srcRect: common2D.Rect = {
    left: 0,
    top: 0,
    right: 1,
    bottom: 1
  };
  let dstRect: common2D.Rect = {
    left: 0,
    top: 0,
    right: 1,
    bottom: 1
  };
  let fillColor: uiEffect.Color = {
    red: 0,
    green: 0,
    blue: 0,
    alpha: 1
  };
  let mask = uiEffect.Mask.createPixelMapMask(pixelMap, srcRect, dstRect, fillColor);
}).catch((error: BusinessError)=>{
  console.error(`Failed to create pixelmap. code is ${error.code}, message is ${error.message}`);
});
```

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';
import { image } from '@kit.ImageKit';
import { common } from '@kit.AbilityKit';

@Entry
@Component
struct Index {
  @State distortProgress: number = 0.;
  @State rippleProgress: number = 0.;
  @State distortFactor: number = 0.;
  @State materialFactor: number = 1.;
  @State refractionFactor: number = 1.;
  @State reflectionFactor: number = 1.;
  @State tintColorR: number = 1.;
  @State tintColorG: number = 1.;
  @State tintColorB: number = 1.;
  @State tintColorA: number = 1.;
  @State pixelMapDistort: image.PixelMap | undefined = undefined;

  aboutToAppear(): void {
    this.pixelMapDistort = this.getPixelMap();
  }

  private getPixelMap(): image.PixelMap | undefined {
    try {
      let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
      // this path should be created in local
      const path: string = context.resourceDir + '/perlin_worley_noise_3d_64.bmp';
      const imageSource: image.ImageSource = image.createImageSource(path);
      if (!imageSource) {
        return undefined;
      }
      const pixelMap: image.PixelMap | null = imageSource.createPixelMapSync();
      if (!pixelMap) {
        imageSource.release();
        return undefined;
      }
      imageSource.release();
      return pixelMap;
    } catch (err) {
      return undefined;
    }
  }

  private getMaterialVisualEffect(): uiEffect.VisualEffect {
    let effect: uiEffect.VisualEffect = uiEffect.createEffect();
    let distortMask: uiEffect.Mask | undefined = undefined;
    if (this.pixelMapDistort) {
      distortMask = uiEffect.Mask.createPixelMapMask(this.pixelMapDistort);
    }
    effect.liquidMaterial({
      enable: true,
      distortProgress: this.distortProgress,
      rippleProgress: this.rippleProgress,
      distortFactor: this.distortFactor,
      materialFactor: this.materialFactor,
      refractionFactor: this.refractionFactor,
      reflectionFactor: this.reflectionFactor,
      tintColor: [this.tintColorR, this.tintColorG, this.tintColorB, this.tintColorA],
      ripplePosition: undefined,
    },
      uiEffect.Mask.createUseEffectMask(true),
      distortMask
      );
    return effect;
  }

  build() {
    Stack() {
      EffectComponent() {
        Column()
          .position({ x: 200 + 'px', y: 200 + 'px' })
          .height(553 + 'px')
          .width(553 + 'px')
          .borderRadius(12)
          .visualEffect(this.getMaterialVisualEffect())
      }
      .backgroundEffect({
        radius: 15,
      }, { disableSystemAdaptation: true })
      .width('100%').height('100%').align(Alignment.Center)
    }
    .backgroundImage($r('app.media.bg6'), ImageRepeat.NoRepeat) // the image should be created in local
    .width('100%').height('100%').align(Alignment.Center)
  }
}
```

## createPixelMapMask

```TypeScript
static createPixelMapMask(pixelMap: image.PixelMap): Mask
```

Creates a Mask instance by inputting a pixelMap. This interface does not perform scaling on the input pixelMap.

**Since:** 22

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| pixelMap | [image.PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md) | Yes | The PixelMap instance created by the image module. It can be obtained through image decoding or direct creation. |

**Return value:**

| Type | Description |
| --- | --- |
| [Mask](arkts-arkgraphics2d-uieffect-mask-c-sys.md) | Returns a Mask with the pixelMap. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

See [createPixelMapMask](#createpixelmapmask)

## createRadialGradientMask

```TypeScript
static createRadialGradientMask(center: common2D.Point, radiusX: number, radiusY: number,
      gradients: Array<[number, number]>): Mask
```

Creates an elliptical mask Mask instance by inputting the center position of the ellipse, the semi-major and semi-minor axes, and shape parameters.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| center | [common2D.Point](arkts-arkgraphics2d-common2d-point-i.md) | Yes | Sets the center point of the ellipse. [0, 0] is the top-left corner of the component, [1, 1] is the bottom-right corner of the component. The value range is [-10, 10], floating-point values are supported, and values outside the range will be clamped during implementation. |
| radiusX | number | Yes | Sets the semi-major axis of the ellipse. When the radius is 1, it equals the component height. The value range is [0, 10], floating-point values are supported, and values outside the range will be clamped during implementation. |
| radiusY | number | Yes | Sets the semi-minor axis of the ellipse. When the radius is 1, it equals the component height. The value range is [0, 10], floating-point values are supported, and values outside the range will be clamped during implementation. |
| gradients | Array&lt;[number, number]&gt; | Yes | The binary arrays in the array represent gradients: [RGBA color, position]. The RGBA color uses the same value for all four channels, which can be regarded as a grayscale value; position represents the distribution position of the RGBA color along the radial direction outward. Both RGBA color and position have a value range of [0, 1], floating-point values are supported, values less than 0 are treated as 0, and values greater than 1 are treated as 1. The position parameter values must be strictly increasing, the number of binary arrays in the Array must be greater than or equal to 2, and the elements in the binary arrays must not be empty; otherwise the elliptical distribution effect will not take effect. |

**Return value:**

| Type | Description |
| --- | --- |
| [Mask](arkts-arkgraphics2d-uieffect-mask-c-sys.md) | Returns a grayscale Mask with the elliptical radial distribution effect. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';
// values: [[1.0, 0.5], [1.0, 1.0]] => color0: 1.0; color1: 1.0; position0: 0.5; position1: 1.0
let mask = uiEffect.Mask.createRadialGradientMask({x: 0.0, y: 0.0}, 0.5, 0.5, [[1.0, 0.5], [1.0, 1.0]]);
@Entry
@Component
struct RadialGradientMaskExample {
  build() {
    Stack() {
      Image($rawfile('test.jpg'))
      Column()
        .width('100%')
        .height('100%')
        // Use the mask as the input parameter of the filter to implement the corresponding effect. The mask is a quarter circle ring in the upper left corner of the screen.
        .backgroundFilter(uiEffect.createFilter().edgeLight(1.0, null, mask))
    }
  }
}
```

## createRippleMask

```TypeScript
static createRippleMask(center: common2D.Point, radius: number, width: number, offset?: number): Mask
```

Creates a wave ring mask Mask instance by inputting the center position, radius, and width of the wave ring.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| center | [common2D.Point](arkts-arkgraphics2d-common2d-point-i.md) | Yes | Sets the position of the wave ring center on the component. [0, 0] is the top-left corner of the component, [1, 1] is the bottom-right corner of the component. The value range is [-10, 10], and values outside the range will be clamped during implementation. |
| radius | number | Yes | Sets the radius of the wave ring, using normalized values. When the radius is 1, the wave ring radius equals the component height. The value range is [0, 10], and values outside the range will be clamped during implementation. |
| width | number | Yes | Sets the width of the wave ring, using normalized values. When the width is 1, the wave ring width equals the component height. The value range is [0, 10], and values outside the range will be clamped during implementation. |
| offset | number | No | Sets the offset of the wave peak position. The default value is 0, meaning the wave peak is at the exact center of the wave ring; -1.0 means the wave peak is at the innermost edge of the wave ring; 1.0 means the wave peak is at the outermost edge of the wave ring. The value range is [-1, 1], and values outside the range will be clamped during implementation. |

**Return value:**

| Type | Description |
| --- | --- |
| [Mask](arkts-arkgraphics2d-uieffect-mask-c-sys.md) | Returns a Mask with the wave ring mask effect. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

```TypeScript
let mask = uiEffect.Mask.createRippleMask({x: 0.5, y: 1.0}, 0.5, 0.3, 0.0);
```

## createSweepRefractionMask

```TypeScript
static createSweepRefractionMask(param: SweepRefractionParam, options?: SweepRefractionMaskOptions): Mask
```

Creates a sweep refraction mask Mask instance that simulates a prism-like chromatic dispersion effect. The mask generates a sweeping light band with color separation across the component.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| param | [SweepRefractionParam](arkts-arkgraphics2d-uieffect-sweeprefractionparam-i-sys.md) | Yes | Required parameters including mask radius, edge thickness, refraction amount, ripple width, sweep offset, and chroma delta. |
| options | [SweepRefractionMaskOptions](arkts-arkgraphics2d-uieffect-sweeprefractionmaskoptions-i-sys.md) | No | Optional parameters for the sweep refraction mask, including prism shape, corner radius, prism dimensions, and sweep center. |

**Return value:**

| Type | Description |
| --- | --- |
| [Mask](arkts-arkgraphics2d-uieffect-mask-c-sys.md) | Returns a Mask with the sweep refraction effect. |

## createUseEffectMask

```TypeScript
static createUseEffectMask(useEffect: boolean): Mask
```

Creates and sets a Mask instance indicating whether to use blur caching. This Mask instance is specifically designed for the useEffectMask parameter of the liquidMaterial method, used to declare whether the material effect uses blur caching to improve performance. When this Mask instance is used with other Filter or VisualEffect methods, the useEffect property may not take effect.

**Since:** 22

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| useEffect | boolean | Yes | Flag indicating whether to use blur caching. A value of true means use, and the blur effect will be displayed normally; a value of false means not use, and the blur effect will not be displayed. |

**Return value:**

| Type | Description |
| --- | --- |
| [Mask](arkts-arkgraphics2d-uieffect-mask-c-sys.md) | Returns a Mask instance that indicates whether to use blur caching. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';

@Entry
@Component
struct Index {
  @State distortProgress: number = 0.;
  @State rippleProgress: number = 0.;
  @State distortFactor: number = 0.;
  @State materialFactor: number = 1.;
  @State refractionFactor: number = 1.;
  @State reflectionFactor: number = 1.;
  @State tintColorR: number = 1.;
  @State tintColorG: number = 1.;
  @State tintColorB: number = 1.;
  @State tintColorA: number = 1.;

  private getMaterialVisualEffect(): uiEffect.VisualEffect {
    let effect: uiEffect.VisualEffect = uiEffect.createEffect();
    effect.liquidMaterial({
        enable: true,
        distortProgress: this.distortProgress,
        rippleProgress: this.rippleProgress,
        distortFactor: this.distortFactor,
        materialFactor: this.materialFactor,
        refractionFactor: this.refractionFactor,
        reflectionFactor: this.reflectionFactor,
        tintColor: [this.tintColorR, this.tintColorG, this.tintColorB, this.tintColorA],
        ripplePosition: undefined,
      },
      uiEffect.Mask.createUseEffectMask(true), // Example of using useEffectMask.
    );
    return effect;
  }

  build() {
    Stack() {
      EffectComponent() {
        Column()
          .position({ x: 200 + 'px', y: 200 + 'px' })
          .height(553 + 'px')
          .width(553 + 'px')
          .borderRadius(12)
          .visualEffect(this.getMaterialVisualEffect())
      }
      .backgroundEffect({
        radius: 15,
      }, { disableSystemAdaptation: true })
      .width('100%').height('100%').align(Alignment.Center)
    }
    .backgroundImage($r('app.media.bg6'), ImageRepeat.NoRepeat)
    .width('100%').height('100%').align(Alignment.Center)
  }
}
```

## createWarpedRingMask

```TypeScript
static createWarpedRingMask(ringParam: WarpedRingParam): Mask
```

Creates a Mask instance representing a warped ring.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| ringParam | [WarpedRingParam](arkts-arkgraphics2d-uieffect-warpedringparam-i-sys.md) | Yes | Configures the warped ring's shape. |

**Return value:**

| Type | Description |
| --- | --- |
| [Mask](arkts-arkgraphics2d-uieffect-mask-c-sys.md) | Returns a Mask with the warped ring mask effect. |

## createWaveGradientMask

```TypeScript
static createWaveGradientMask(center: common2D.Point, width: number, propagationRadius: number,
      blurRadius: number, turbulenceStrength?: number): Mask
```

Creates a single-wave mask Mask instance by inputting the wave source center position and single-wave parameters.

**Since:** 20

**System capability:** SystemCapability.Graphics.Drawing

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| center | [common2D.Point](arkts-arkgraphics2d-common2d-point-i.md) | Yes | Sets the center point of the single-wave source. [0, 0] is the top-left corner of the component, [1, 1] is the bottom-right corner of the component. The value range is [-10, 10], floating-point values are supported, and values outside the range will be clamped during implementation. |
| width | number | Yes | Sets the width of the single-wave ring. The value range is [0, 5], floating-point values are supported, and values outside the range will be clamped during implementation. |
| propagationRadius | number | Yes | Sets the outer diffusion radius of the single-wave ring. The value range is [0, 10], floating-point values are supported, and values outside the range will be clamped during implementation. |
| blurRadius | number | Yes | Sets the blur outer radius of the single-wave ring. A blur radius of 0 results in a solid-edge ring; otherwise, it is a soft-edge ring. The value range is [0, 5], floating-point values are supported, and values outside the range will be clamped during implementation. |
| turbulenceStrength | number | No | Sets the turbulence intensity of the single-wave ring. The default value is 0; an intensity of 0 results in a regular ring, otherwise the ring edges will be turbulently distorted. The value range is [-1, 1], floating-point values are supported, and values outside the range will be clamped during implementation. |

**Return value:**

| Type | Description |
| --- | --- |
| [Mask](arkts-arkgraphics2d-uieffect-mask-c-sys.md) | Returns a grayscale Mask with a single wave shape. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

```TypeScript
import { uiEffect } from '@kit.ArkGraphics2D';
// center: [0.5, 0.5]; width: 0.01; propagationRadius: 0.5; blurRadius: 0.1; turbulenceStrength: 0.1
let mask = uiEffect.Mask.createWaveGradientMask({x: 0.5, y: 0.5}, 0.01, 0.5, 0.1, 0.1);
@Entry
@Component
struct WaveGradientMaskExample {
  build() {
    Stack() {
      Image($rawfile('test.jpg'))
      Column()
        .width('100%')
        .height('100%')
        // Use the mask as the filter parameter to implement the ripple effect that spreads from the center of the screen.
        .backgroundFilter(uiEffect.createFilter().edgeLight(1.0, null, mask))
    }
  }
}
```
