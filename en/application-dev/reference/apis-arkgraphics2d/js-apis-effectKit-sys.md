# @ohos.effectKit (Image Effect) (System API)

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Multimedia-->
<!--Owner: @hanamaru-->
<!--Designer: @gaoweihua-->
<!--Tester: @zhaoxiaoguang2-->
<!--Adviser: @ge-yafang-->

This module provides basic image processing capabilities, including brightness adjustment, blurring, grayscale adjustment, and color picker. The **effectKit** module processes images (such as PixelMap, PNG, and JPEG) offline to obtain visual effects. The **uiEffect** module connects to the rendering service in real time and process the screen frame buffer to obtain dynamic visual effects.

This module provides the [ColorPicker](#colorpicker) class, which is a smart color picker.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - This topic describes only system APIs provided by the module. For details about its public APIs, see [@ohos.effectKit (Image Effects)](js-apis-effectKit.md).

## Modules to Import

```ts
import { effectKit } from "@kit.ArkGraphics2D";
```

## PictureComplexityDegree<sup>22+</sup>

Enumerates levels of image content complexity.

**System capability**: SystemCapability.Multimedia.Image.Core

**System API**: This is a system API.

| Name                  | Value  | Description                          |
| ---------------------- | ---- | ------------------------------ |
| UNKNOWN_COMPLEXITY_DEGREE_PICTURE | 0 | Default value. The image content complexity is unknown.|
| PURE_PICTURE    | 1    | The image content complexity is pure.|
| MODERATE_COMPLEXITY_PICTURE    | 2    | The image content complexity is moderate.|
| VERY_FLOWERY_PICTURE     | 3    | The image content complexity is complex.|

## PictureShadeDegree<sup>22+</sup>

Enumerates image color shade levels.

**System capability**: SystemCapability.Multimedia.Image.Core

**System API**: This is a system API.

| Name                  | Value  | Description                          |
| ---------------------- | ---- | ------------------------------ |
| UNKNOWN_SHADE_DEGREE_PICTURE     | 0    | Default value. The image color shade level is unknown.|
| EXTREMELY_LIGHT_PICTURE    | 1    | The image color shade level is extremely light.|
| VERY_LIGHT_PICTURE    | 2    | The image color shade level is very light.|
| LIGHT_PICTURE     | 3    | The image color shade level is light.|
| MODERATE_SHADE_PICTURE     | 4    | The image color shade level is moderate.|
| DARK_PICTURE     | 5    | The image color shade level is dark.|
| EXTREMELY_DARK_PICTURE     | 6    | The image color shade level is extremely dark.|

## ColorPicker

A class used to obtain the color from an image. Before calling any method of **ColorPicker**, use [createColorPicker](js-apis-effectKit.md#effectkitcreatecolorpicker) to create a **ColorPicker** instance.

### getTopProportionColorsAndPercentage<sup>22+</sup>

getTopProportionColorsAndPercentage(colorCount: number): Map<Color | null, number | null>

Reads the color values with the top proportions in an image and their corresponding proportions. The number of colors to obtain is specified by **colorCount**, and the results are stored in a dictionary mapping **Color** values to their respective proportions, returned synchronously.

**Widget capability**: This API can be used in ArkTS widgets since API version 22.

**System capability**: SystemCapability.Multimedia.Image.Core

**System API**: This is a system API.

**Parameters**
| Name     | Type  | Mandatory| Description             |
| ---------- | ------ | ---- | ------------------------------------------- |
| colorCount | number | Yes  | Number of colors to be obtained. The value is rounded down.  |

**Return value**

| Type                                    | Description                                           |
| :--------------------------------------- | :---------------------------------------------- |
| Map<Color \| null, number \| null> | Dictionary containing the top-proportion colors in the image and their corresponding proportions, with the number of colors specified by **colorCount**. The proportion value range is [0, 1].<br>- If the number of colors obtained is less than the value of **colorCount**, the size of the dictionary matches the actual number of colors.<br>- If the colors fail to be obtained or the number of colors obtained is less than 1, **Map()** is returned.<br>- If the number of colors to be obtained exceeds 10, only the top 10 colors are retained.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 202  | Permission verification failed. A non-system application calls a system API. |

**Example**

```js
import { image } from "@kit.ImageKit";
import { effectKit } from "@kit.ArkGraphics2D";

const color = new ArrayBuffer(96);
let opts: image.InitializationOptions = {
  editable: true,
  pixelFormat: 3,
  size: {
    height: 4,
    width: 6
  }
}
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
  })
})
```
![image_Top_Proportion_Colors_And_Percentages.png](figures/image_Top_Proportion_Colors_And_Percentages.png)

### getShadeDegree<sup>22+</sup>

getShadeDegree(): PictureShadeDegree

Obtains the color shade level of an image.

**Widget capability**: This API can be used in ArkTS widgets since API version 22.

**System capability**: SystemCapability.Multimedia.Image.Core

**System API**: This is a system API.

**Return value**

| Type                                    | Description                                           |
| :--------------------------------------- | :---------------------------------------------- |
| [PictureShadeDegree](#pictureshadedegree22) | Image color shade level.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 202  | Permission verification failed. A non-system application calls a system API. |

**Example**

```js
import { image } from "@kit.ImageKit";
import { effectKit } from "@kit.ArkGraphics2D";

const color = new ArrayBuffer(96);
let opts: image.InitializationOptions = {
  editable: true,
  pixelFormat: 3,
  size: {
    height: 4,
    width: 6
  }
}
image.createPixelMap(color, opts).then((pixelMap) => {
  effectKit.createColorPicker(pixelMap, (error, colorPicker) => {
    if (error) {
      console.error('Failed to create color picker.');
    } else {
      console.info('Succeeded in creating color picker.');
      let shadeDegree: effectKit.PictureShadeDegree = colorPicker.getShadeDegree();
      console.info('The shade degree of the image is ' + shadeDegree);
    }
  })
})
```

### getComplexityDegree<sup>22+</sup>

getComplexityDegree(): PictureComplexityDegree

Obtains the image content complexity.

**Widget capability**: This API can be used in ArkTS widgets since API version 22.

**System capability**: SystemCapability.Multimedia.Image.Core

**System API**: This is a system API.

**Return value**

| Type                                    | Description                                           |
| :--------------------------------------- | :---------------------------------------------- |
| [PictureComplexityDegree](#picturecomplexitydegree22) | Image content complexity.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------- |
| 202  | Permission verification failed. A non-system application calls a system API. |

**Example**

```js
import { image } from "@kit.ImageKit";
import { effectKit } from "@kit.ArkGraphics2D";

const color = new ArrayBuffer(96);
let opts: image.InitializationOptions = {
  editable: true,
  pixelFormat: 3,
  size: {
    height: 4,
    width: 6
  }
}
image.createPixelMap(color, opts).then((pixelMap) => {
  effectKit.createColorPicker(pixelMap, (error, colorPicker) => {
    if (error) {
      console.error('Failed to create color picker.');
    } else {
      console.info('Succeeded in creating color picker.');
      let complexityDegree: effectKit.PictureComplexityDegree = colorPicker.getComplexityDegree();
      console.info('The complexity degree of the image is ' + complexityDegree);
    }
  })
})
```
