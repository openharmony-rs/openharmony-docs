# Class (ColorFilter)

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->

颜色滤波器，用于对图像或图形的颜色进行变换和处理，支持创建混合模式颜色滤波器、组合颜色滤波器、矩阵颜色滤波器、伽马颜色空间转换滤波器、亮度颜色滤波器和光照颜色滤波器等多种类型，适用于图像处理、视觉效果渲染等需要对颜色进行变换和滤镜处理的场景。

> **说明：**
>
> - 本模块首批接口从API version 11开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 本模块使用屏幕物理像素单位px。
>
> - 本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。

## 导入模块

```ts
import { drawing } from '@kit.ArkGraphics2D';
```

## createBlendModeColorFilter

static createBlendModeColorFilter(color: common2D.Color, mode: BlendMode) : ColorFilter

创建指定的颜色和混合模式的颜色滤波器。适用于需要将指定颜色以特定混合模式叠加到目标内容上的场景，如实现颜色蒙版、图像着色等效果。

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型                                                 | 必填 | 说明             |
| ------ | ---------------------------------------------------- | ---- | ---------------- |
| color  | [common2D.Color](js-apis-graphics-common2D.md#color) | 是   | ARGB格式的颜色，每个颜色通道的值是[0, 255]的整数。 |
| mode   | [BlendMode](arkts-apis-graphics-drawing-e.md#blendmode)                              | 是   | 混合模式，用于指定两个着色器叠加时的颜色混合算法。 |

**返回值：**

| 类型                        | 说明               |
| --------------------------- | ------------------ |
| [ColorFilter](arkts-apis-graphics-drawing-ColorFilter.md) | 返回基于指定颜色和混合模式创建的颜色滤波器，可用于对图像进行颜色混合滤波处理。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types;3.Parameter verification failed. |

**示例：**

```ts
import { common2D, drawing } from '@kit.ArkGraphics2D';

const color : common2D.Color = { alpha: 255, red: 255, green: 0, blue: 0 };
let colorFilter = drawing.ColorFilter.createBlendModeColorFilter(color, drawing.BlendMode.SRC);
```

## createBlendModeColorFilter<sup>18+</sup>

static createBlendModeColorFilter(color: common2D.Color | number, mode: BlendMode) : ColorFilter

创建指定的颜色和混合模式的颜色滤波器。适用于需要将指定颜色以特定混合模式叠加到目标内容上的场景，如实现颜色蒙版、图像着色等效果。

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型                                                 | 必填 | 说明             |
| ------ | ---------------------------------------------------- | ---- | ---------------- |
| color  | [common2D.Color](js-apis-graphics-common2D.md#color) \| number | 是   | 颜色。为common2D.Color类型时，每个颜色通道的值是[0, 255]的整数；为number类型时，用16进制ARGB格式的无符号整数表示，取值范围为[0, 0xFFFFFFFF]。 |
| mode   | [BlendMode](arkts-apis-graphics-drawing-e.md#blendmode)                              | 是   | 混合模式，用于指定两个着色器叠加时的颜色混合算法。 |

**返回值：**

| 类型                        | 说明               |
| --------------------------- | ------------------ |
| [ColorFilter](arkts-apis-graphics-drawing-ColorFilter.md) | 返回基于指定颜色和混合模式创建的颜色滤波器，可用于对图像进行颜色混合滤波处理。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types;3.Parameter verification failed. |

**示例：**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let colorFilter = drawing.ColorFilter.createBlendModeColorFilter(0xffff0000, drawing.BlendMode.SRC);
```

## createComposeColorFilter

static createComposeColorFilter(outer: ColorFilter, inner: ColorFilter) : ColorFilter

创建一个先应用inner进行滤波，再应用outer进行滤波的组合颜色滤波器。适用于需要将多个颜色滤波效果叠加的场景，如同时应用颜色矩阵变换和混合模式滤镜以实现复杂的颜色处理效果。

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型                        | 必填 | 说明                             |
| ------ | --------------------------- | ---- | -------------------------------- |
| outer  | [ColorFilter](arkts-apis-graphics-drawing-ColorFilter.md) | 是   | 组合滤波器中后生效的颜色滤波器。 |
| inner  | [ColorFilter](arkts-apis-graphics-drawing-ColorFilter.md) | 是   | 组合滤波器中先生效的颜色滤波器。 |

**返回值：**

| 类型                        | 说明               |
| --------------------------- | ------------------ |
| [ColorFilter](arkts-apis-graphics-drawing-ColorFilter.md) |返回创建的组合颜色滤波器，该滤波器会先应用inner再应用outer进行颜色滤波。|

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**示例：**

```ts
import { common2D, drawing } from '@kit.ArkGraphics2D';

const color : common2D.Color = { alpha: 255, red: 255, green: 0, blue: 0 };
let colorFilter1 = drawing.ColorFilter.createBlendModeColorFilter(color, drawing.BlendMode.SRC);
let colorFilter2 = drawing.ColorFilter.createBlendModeColorFilter(color, drawing.BlendMode.DST);
let colorFilter = drawing.ColorFilter.createComposeColorFilter(colorFilter1, colorFilter2);
```

## createLinearToSRGBGamma

static createLinearToSRGBGamma() : ColorFilter

创建一个从线性颜色空间转换到SRGB颜色空间的颜色滤波器。适用于在线性颜色空间中完成计算后，需要将结果转换回SRGB颜色空间以正确显示的场景。

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型                        | 说明               |
| --------------------------- | ------------------ |
| [ColorFilter](arkts-apis-graphics-drawing-ColorFilter.md) | 返回创建的颜色滤波器，可用于将线性颜色空间转换到SRGB颜色空间。 |

**示例：**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let colorFilter = drawing.ColorFilter.createLinearToSRGBGamma();
```

## createSRGBGammaToLinear

static createSRGBGammaToLinear() : ColorFilter

创建一个从SRGB颜色空间转换到线性颜色空间的颜色滤波器。适用于需要在线性颜色空间中进行颜色计算（如混合、光照等）前，先将SRGB输入转换到线性空间的场景。

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型                        | 说明               |
| --------------------------- | ------------------ |
| [ColorFilter](arkts-apis-graphics-drawing-ColorFilter.md) | 返回创建的颜色滤波器，可用于将SRGB颜色空间转换到线性颜色空间。 |

**示例：**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let colorFilter = drawing.ColorFilter.createSRGBGammaToLinear();
```

## createLumaColorFilter

static createLumaColorFilter() : ColorFilter

创建一个颜色滤波器将其输入的亮度值乘以透明度通道的值，并将红色、绿色和蓝色通道设置为零。适用于需要提取图像亮度信息作为蒙版或阴影效果的场景，如实现基于亮度的遮罩。

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型                        | 说明               |
| --------------------------- | ------------------ |
| [ColorFilter](arkts-apis-graphics-drawing-ColorFilter.md) | 返回创建的颜色滤波器，可将输入的亮度值乘以透明度通道的值并将RGB通道置零。 |

**示例：**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let colorFilter = drawing.ColorFilter.createLumaColorFilter();
```

## createMatrixColorFilter<sup>12+</sup>

static createMatrixColorFilter(matrix: Array\<number>): ColorFilter

创建颜色滤波器，通过4×5颜色矩阵变换颜色。适用于需要自定义颜色变换的场景，如实现灰度化、色彩校正、色调调整、复古滤镜等效果。

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名   | 类型                                         | 必填 | 说明                            |
| -------- | -------------------------------------------- | ---- | ------------------------------- |
| matrix | Array\<number> | 是   | 长度为20的数组，表示用于颜色变换的4×5矩阵。                 |

**返回值：**

| 类型                        | 说明               |
| --------------------------- | ------------------ |
| [ColorFilter](arkts-apis-graphics-drawing-ColorFilter.md) | 返回创建的颜色滤波器，通过4×5颜色矩阵对颜色进行变换。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types;3.Parameter verification failed. |

**示例：**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let matrix: Array<number> = [
  1, 0, 0, 0, 0,
  0, 1, 0, 0, 0,
  0, 0, 100, 0, 0,
  0, 0, 0, 1, 0
];
let colorFilter = drawing.ColorFilter.createMatrixColorFilter(matrix);
```
## createLightingColorFilter<sup>20+</sup>

static createLightingColorFilter(mutColor: common2D.Color | number, addColor: common2D.Color | number): ColorFilter

创建一个光照颜色滤波器，此滤波器会将RGB通道的颜色值乘以乘法颜色（mutColor）并加上加法颜色（addColor），计算结果会被限制在0到255范围内。适用于需要模拟光照效果或调整画面亮度色调的场景，如实现高光、阴影等光照滤镜效果。

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名   | 类型                                         | 必填 | 说明                            |
| -------- | -------------------------------------------- | ---- | ------------------------------- |
| mutColor | [common2D.Color](js-apis-graphics-common2D.md#color) \| number | 是   | 用来进行乘法运算的颜色。为common2D.Color类型时，每个颜色通道的值是[0, 255]的整数；为number类型时，用16进制ARGB格式的无符号整数表示，取值范围为[0, 0xFFFFFFFF]。 |
| addColor | [common2D.Color](js-apis-graphics-common2D.md#color) \| number | 是   | 用来进行加法运算的颜色。为common2D.Color类型时，每个颜色通道的值是[0, 255]的整数；为number类型时，用16进制ARGB格式的无符号整数表示，取值范围为[0, 0xFFFFFFFF]。 |

**返回值：**

| 类型                        | 说明                |
| --------------------------- | ------------------ |
| [ColorFilter](arkts-apis-graphics-drawing-ColorFilter.md) | 返回创建的光照颜色滤波器，可将RGB通道颜色值乘以一种颜色并加上另一种颜色实现光照效果。 |

**示例：**

```ts
import { common2D, drawing } from '@kit.ArkGraphics2D';
let mulColor : common2D.Color = { alpha: 0, red: 0, green: 0, blue: 20 };
let addColor : common2D.Color = { alpha: 0, red: 0, green: 0, blue: 125 };
let colorFilter = drawing.ColorFilter.createLightingColorFilter(mulColor, addColor);
```