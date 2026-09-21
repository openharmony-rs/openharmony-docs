# ColorPicker

```TypeScript
interface ColorPicker
```

A color picker class used to obtain the main color from image data. It is suitable for scenarios such as UI theme color extraction, image color scheme analysis, and intelligent color scheme recommendation, helping developers dynamically generate harmonious color schemes based on image content. Before calling the methods of ColorPicker, you need to create a ColorPicker instance via createColorPicker.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Image.Core

## Modules to Import

```TypeScript
import { effectKit } from '@kit.ArkGraphics2D';
```

## discriminatePictureLightDegree

```TypeScript
discriminatePictureLightDegree(): PictureLightDegree
```

Discriminates the light and dark degree of the picture. When the light and dark degree cannot be determined, UNKNOWN_LIGHT_COLOR_DEGREE_PICTURE is returned.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Image.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| [PictureLightDegree](arkts-arkgraphics2d-effectkit-picturelightdegree-e-sys.md) | Light and dark degree of the image. |

**Examples**

```TypeScript
import { image } from '@kit.ImageKit';
import { effectKit } from '@kit.ArkGraphics2D';

const color = new ArrayBuffer(96);
let opts: image.InitializationOptions = {
  editable: true,
  pixelFormat: 3,
  size: {
    height: 4,
    width: 6
  }
};
image.createPixelMap(color, opts).then((pixelMap) => {
  effectKit.createColorPicker(pixelMap, (error, colorPicker) => {
    if (error) {
      console.error('Failed to create color picker.');
    } else {
      console.info('Succeeded in creating color picker.');
      let pictureLightDegree: effectKit.PictureLightDegree = colorPicker.discriminatePictureLightDegree();
      console.info('The color light degree of the image is ' + pictureLightDegree);
    }
  });
});
```

## getAlphaZeroTransparentProportion

```TypeScript
getAlphaZeroTransparentProportion(): number
```

Obtains the proportion of fully transparent pixels with alpha=0 in the image.

**Since:** 23

**Widget capability:** This API can be used in ArkTS widgets since API version 23.

**System capability:** SystemCapability.Multimedia.Image.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| number | Proportion of fully transparent pixels with alpha=0. The value range is [0, 1]. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

```TypeScript
import { image } from '@kit.ImageKit';
import { effectKit } from '@kit.ArkGraphics2D';

const color = new ArrayBuffer(96);
let opts: image.InitializationOptions = {
  editable: true,
  pixelFormat: 3,
  size: {
    height: 4,
    width: 6
  }
};
image.createPixelMap(color, opts).then((pixelMap) => {
  effectKit.createColorPicker(pixelMap, (error, colorPicker) => {
    if (error) {
      console.error('Failed to create color picker.');
    } else {
      console.info('Succeeded in creating color picker.');
        let percentage: number = colorPicker.getAlphaZeroTransparentProportion();
      console.info('Get proportion of fully transparent pixels: ' + percentage);
    }
  });
});
```

## getComplexityDegree

```TypeScript
getComplexityDegree(): PictureComplexityDegree
```

Obtains the complexity degree of the image. When the complexity degree cannot be determined, the default value UNKNOWN_COMPLEXITY_DEGREE_PICTURE is returned.

**Since:** 22

**Widget capability:** This API can be used in ArkTS widgets since API version 22.

**System capability:** SystemCapability.Multimedia.Image.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| [PictureComplexityDegree](arkts-arkgraphics2d-effectkit-picturecomplexitydegree-e-sys.md) | Complexity degree of the image. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

```TypeScript
import { image } from '@kit.ImageKit';
import { effectKit } from '@kit.ArkGraphics2D';

const color = new ArrayBuffer(96);
let opts: image.InitializationOptions = {
  editable: true,
  pixelFormat: 3,
  size: {
    height: 4,
    width: 6
  }
};
image.createPixelMap(color, opts).then((pixelMap) => {
  effectKit.createColorPicker(pixelMap, (error, colorPicker) => {
    if (error) {
      console.error('Failed to create color picker.');
    } else {
      console.info('Succeeded in creating color picker.');
      let complexityDegree: effectKit.PictureComplexityDegree = colorPicker.getComplexityDegree();
      console.info('The complexity degree of the image is ' + complexityDegree);
    }
  });
});
```

## getDeepenImmersionColor

```TypeScript
getDeepenImmersionColor(): Color
```

Generates a stronger immersion color that merges with the background color and is deeper than the background color, and writes the result to a Color instance. This API uses a color mixing algorithm to create a color that is both harmonious with the background color and has a stronger immersive effect.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Image.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| [Color](arkts-arkgraphics2d-effectkit-color-i.md) | Color value of the deepened immersion color. If the image processing fails or the immersion color cannot be generated, null is returned. |

**Examples**

```TypeScript
import { image } from '@kit.ImageKit';
import { effectKit } from '@kit.ArkGraphics2D';

const color = new ArrayBuffer(96);
let opts: image.InitializationOptions = {
  editable: true,
  pixelFormat: 3,
  size: {
    height: 4,
    width: 6
  }
};
image.createPixelMap(color, opts).then((pixelMap) => {
  effectKit.createColorPicker(pixelMap, (error, colorPicker) => {
    if (error) {
      console.error('Failed to create color picker.');
    } else {
      console.info('Succeeded in creating color picker.');
      let color = colorPicker.getDeepenImmersionColor();
      console.info('get deepen immersion color =' + color);
    }
  });
});
```

## getImmersiveBackgroundColor

```TypeScript
getImmersiveBackgroundColor(): Color
```

Generates an immersive background color that creates an immersive visual effect, and writes the result to a Color instance. This API generates a color value suitable for use as an immersive background based on the dominant color.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Image.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| [Color](arkts-arkgraphics2d-effectkit-color-i.md) | Color value of the immersive background color. If the image processing fails or the immersive background color cannot be generated, null is returned. |

**Examples**

```TypeScript
import { image } from '@kit.ImageKit';
import { effectKit } from '@kit.ArkGraphics2D';

const color = new ArrayBuffer(96);
let opts: image.InitializationOptions = {
  editable: true,
  pixelFormat: 3,
  size: {
    height: 4,
    width: 6
  }
};
image.createPixelMap(color, opts).then((pixelMap) => {
  effectKit.createColorPicker(pixelMap, (error, colorPicker) => {
    if (error) {
      console.error('Failed to create color picker.');
    } else {
      console.info('Succeeded in creating color picker.');
      let color = colorPicker.getImmersiveBackgroundColor();
      console.info('get immersive background color =' + color);
    }
  })
});
```

## getImmersiveForegroundColor

```TypeScript
getImmersiveForegroundColor(): Color
```

Generates an immersive foreground color that creates an immersive visual effect for text and content, and writes the result to a Color instance. This API generates a color value suitable for use as an immersive foreground based on the dominant color.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Image.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| [Color](arkts-arkgraphics2d-effectkit-color-i.md) | Color value of the immersive foreground color. If the image processing fails or the immersive foreground color cannot be generated, null is returned. |

**Examples**

```TypeScript
import { image } from '@kit.ImageKit';
import { effectKit } from '@kit.ArkGraphics2D';

const color = new ArrayBuffer(96);
let opts: image.InitializationOptions = {
  editable: true,
  pixelFormat: 3,
  size: {
    height: 4,
    width: 6
  }
};
image.createPixelMap(color, opts).then((pixelMap) => {
  effectKit.createColorPicker(pixelMap, (error, colorPicker) => {
    if (error) {
      console.error('Failed to create color picker.');
    } else {
      console.info('Succeeded in creating color picker.');
      let color = colorPicker.getImmersiveForegroundColor();
      console.info('get immersive foreground color =' + color);
    }
  });
});
```

## getMorandiShadowColor

```TypeScript
getMorandiShadowColor(): Color
```

Obtains the Morandi shadow color from the dominant color of the image and writes the result to a Color instance. This API uses a specific color conversion algorithm to convert the dominant color into a Morandi style shadow tone.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Image.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| [Color](arkts-arkgraphics2d-effectkit-color-i.md) | Color value of the Morandi shadow color. If the image processing fails or the Morandi shadow color cannot be obtained, null is returned. |

**Examples**

```TypeScript
import { image } from '@kit.ImageKit';
import { effectKit } from '@kit.ArkGraphics2D';

const color = new ArrayBuffer(96);
let opts: image.InitializationOptions = {
  editable: true,
  pixelFormat: 3,
  size: {
    height: 4,
    width: 6
  }
};
image.createPixelMap(color, opts).then((pixelMap) => {
  effectKit.createColorPicker(pixelMap, (error, colorPicker) => {
    if (error) {
      console.error('Failed to create color picker.');
    } else {
      console.info('Succeeded in creating color picker.');
      let color = colorPicker.getMorandiShadowColor();
      console.info('get Morandi shadow color =' + color);
    }
  });
});
```

## getReverseColor

```TypeScript
getReverseColor(): Color
```

Generates a reverse color based on the image brightness discrimination result, and writes the result to a Color instance. Based on the image light degree type obtained from the discriminatePictureLightDegree API, a reverse color is generated. Only the extremely light color picture (EXTREMELY_LIGHT_COLOR_PICTURE) type returns black; other types return white. It is used for UI themes or contrast calculations.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Image.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| [Color](arkts-arkgraphics2d-effectkit-color-i.md) | Color value of the reverse color. If the image processing fails or the reverse color cannot be generated, null is returned. |

**Examples**

```TypeScript
import { image } from '@kit.ImageKit';
import { effectKit } from '@kit.ArkGraphics2D';

const color = new ArrayBuffer(96);
let opts: image.InitializationOptions = {
  editable: true,
  pixelFormat: 3,
  size: {
    height: 4,
    width: 6
  }
};
image.createPixelMap(color, opts).then((pixelMap) => {
  effectKit.createColorPicker(pixelMap, (error, colorPicker) => {
    if (error) {
      console.error('Failed to create color picker.');
    } else {
      console.info('Succeeded in creating color picker.');
      let color = colorPicker.getReverseColor();
      console.info('get reverse color =' + color);
    }
  });
});
```

## getShadeDegree

```TypeScript
getShadeDegree(): PictureShadeDegree
```

Obtains the shade degree of the image. When the shade degree cannot be determined, the default value UNKNOWN_SHADE_DEGREE_PICTURE is returned.

**Since:** 22

**Widget capability:** This API can be used in ArkTS widgets since API version 22.

**System capability:** SystemCapability.Multimedia.Image.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| [PictureShadeDegree](arkts-arkgraphics2d-effectkit-pictureshadedegree-e-sys.md) | Shade degree of the image. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

```TypeScript
import { image } from '@kit.ImageKit';
import { effectKit } from '@kit.ArkGraphics2D';

const color = new ArrayBuffer(96);
let opts: image.InitializationOptions = {
  editable: true,
  pixelFormat: 3,
  size: {
    height: 4,
    width: 6
  }
};
image.createPixelMap(color, opts).then((pixelMap) => {
  effectKit.createColorPicker(pixelMap, (error, colorPicker) => {
    if (error) {
      console.error('Failed to create color picker.');
    } else {
      console.info('Succeeded in creating color picker.');
      let shadeDegree: effectKit.PictureShadeDegree = colorPicker.getShadeDegree();
      console.info('The shade degree of the image is ' + shadeDegree);
    }
  });
});
```

## getTopProportionColorsAndPercentage

```TypeScript
getTopProportionColorsAndPercentage(colorCount: number): Map<Color | null, number | null>
```

Synchronously returns the top proportion colors and their corresponding percentages from the image, with the number specified by colorCount.

**Since:** 22

**Widget capability:** This API can be used in ArkTS widgets since API version 22.

**System capability:** SystemCapability.Multimedia.Image.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| colorCount | number | Yes | Number of color values and their corresponding percentages, rounded down. Before OpenHarmony 6.1, the value range is [1, 10]. If the number of colors to extract is greater than 10, the top 10 are taken. Since OpenHarmony 6.1, the value range is [1, 20]. If the number of colors to extract is greater than 20, the top 20 are taken. |

**Return value:**

| Type | Description |
| --- | --- |
| Map&lt;[Color](arkts-arkgraphics2d-effectkit-color-i.md) &#124; null, number &#124; null&gt; | Map of the top colorCount color values and their corresponding percentages by proportion in the image. The percentage value range is [0, 1].   - If the number of colors obtained is less than the value of colorCount, the map size is the actual   number obtained.   - If the colors fail to be obtained or the number of colors obtained is less than 1, Map() is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |

**Examples**

```TypeScript
import { image } from '@kit.ImageKit';
import { effectKit } from '@kit.ArkGraphics2D';

const color = new ArrayBuffer(96);
let opts: image.InitializationOptions = {
  editable: true,
  pixelFormat: 3,
  size: {
    height: 4,
    width: 6
  }
};
image.createPixelMap(color, opts).then((pixelMap) => {
  effectKit.createColorPicker(pixelMap, (error, colorPicker) => {
    if (error) {
      console.error('Failed to create color picker.');
    } else {
      console.info('Succeeded in creating color picker.');
      let colors: Map<effectKit.Color | null, number | null> = colorPicker.getTopProportionColorsAndPercentage(2);
      colors.forEach((value: number | null, key: effectKit.Color | null) => {
        console.info('get top proportion colors and percentages: color ' + key + ', percentage ' + value);
      })
    }
  });
});
```
