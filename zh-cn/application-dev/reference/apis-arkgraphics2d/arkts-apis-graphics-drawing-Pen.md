# Class (Pen)

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @hangmengxin-->
<!--Designer: @wangyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->

画笔对象，描述所绘制图形形状的轮廓信息。

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
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

## constructor<sup>12+</sup>

constructor()

构造一个新的画笔对象。

**系统能力：** SystemCapability.Graphics.Drawing

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**示例：**

```ts
import { drawing } from '@kit.ArkGraphics2D';

const pen = new drawing.Pen();
```

## constructor<sup>12+</sup>

constructor(pen: Pen)

复制构造一个新的画笔对象。

**系统能力：** SystemCapability.Graphics.Drawing

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型        | 必填 | 说明              |
| ------| ----------- | ---- | ---------------- |
| pen     | [Pen](arkts-apis-graphics-drawing-Pen.md) | 是   | 待复制的画笔对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**示例：**

```ts
import { common2D, drawing } from '@kit.ArkGraphics2D';

const pen = new drawing.Pen();
const penColor: common2D.Color = { alpha: 255, red: 0, green: 255, blue: 0 };
pen.setColor(penColor);
pen.setStrokeWidth(10.0);
const newPen = new drawing.Pen(pen);
```

## setMiterLimit<sup>12+</sup>

ArkTS-Dyn: setMiterLimit(miter: number): void

ArkTS-Sta: setMiterLimit(miter: double): void

设置折线尖角长度与线宽的最大比值，当画笔绘制一条折线，并且[JoinStyle](arkts-apis-graphics-drawing-e.md#joinstyle12)为MITER_JOIN时，若尖角长度与线宽的比值大于限制值，则该折角使用BEVEL_JOIN绘制。

**系统能力：** SystemCapability.Graphics.Drawing

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型    | 必填 | 说明              |
| ------ | ------ | ---- | ---------------- |
| miter  | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 是   | 折线尖角长度与线宽的最大比值，负数在绘制时会被视作4.0处理，非负数正常生效，该参数为浮点数。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**示例：**

```ts
import { drawing } from '@kit.ArkGraphics2D';

const pen = new drawing.Pen();
pen.setMiterLimit(5.0);
```

## getMiterLimit<sup>12+</sup>

ArkTS-Dyn: getMiterLimit(): number

ArkTS-Sta: getMiterLimit(): double

获取折线尖角的限制值。

**系统能力：** SystemCapability.Graphics.Drawing

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型   | 说明                 |
| -------| -------------------- |
| ArkTS-Dyn: number<br/>ArkTS-Sta: double | 返回折线尖角长度与线宽的最大比值。 |

**示例：**

```ts
import { drawing } from '@kit.ArkGraphics2D';

const pen = new drawing.Pen();
let miter = pen.getMiterLimit();
```

## setImageFilter<sup>12+</sup>

setImageFilter(filter: ImageFilter | null): void

设置画笔的图像滤波器。

**系统能力：** SystemCapability.Graphics.Drawing

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型   | 必填 | 说明                    |
| ------ | ------ | ---- | ----------------------- |
| filter    | [ImageFilter](arkts-apis-graphics-drawing-ImageFilter.md) \| null | 是   |  图像滤波器，null表示清空画笔的图像滤波器效果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;2. Incorrect parameter types. |

**示例：**

ArkTS-Dyn示例：
```ts
import { drawing } from '@kit.ArkGraphics2D';

let colorfilter = drawing.ColorFilter.createSRGBGammaToLinear();
let imgFilter = drawing.ImageFilter.createFromColorFilter(colorfilter);
let pen = new drawing.Pen();
pen.setImageFilter(imgFilter);
pen.setImageFilter(null);
```

ArkTS-Sta示例：
```ts
import { drawing } from '@kit.ArkGraphics2D';

let colorfilter = drawing.ColorFilter.createSRGBGammaToLinear();
let imgFilter = colorfilter == undefined ? undefined : drawing.ImageFilter.createFromColorFilter(colorfilter!);
let pen = new drawing.Pen();
if (imgFilter != undefined) {
  pen.setImageFilter(imgFilter!);
}
pen.setImageFilter(null);
```

## getColorFilter<sup>12+</sup>

getColorFilter(): ColorFilter

getColorFilter(): ColorFilter | undefined

获取画笔的颜色滤波器。

**系统能力：** SystemCapability.Graphics.Drawing

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                        | 说明               |
| --------------------------- | ------------------ |
| ArkTS-Dyn: [ColorFilter](arkts-apis-graphics-drawing-ColorFilter.md)<br/>ArkTS-Sta: [ColorFilter](arkts-apis-graphics-drawing-ColorFilter.md) \| undefined | 返回颜色滤波器。获取失败时返回undefined。 |

**示例：**

ArkTS-Dync示例：
```ts 
import { drawing } from '@kit.ArkGraphics2D';

let pen = new drawing.Pen();
let colorfilter = drawing.ColorFilter.createLumaColorFilter();
pen.setColorFilter(colorfilter);
let filter = pen.getColorFilter();
```

ArkTS-Sta示例：
```ts
import { drawing } from '@kit.ArkGraphics2D';

let pen = new drawing.Pen();
let setColorFilter = drawing.ColorFilter.createSRGBGammaToLinear();
if (setColorFilter != undefined) {
  pen.setColorFilter(setColorFilter!);
}
let filter = pen.getColorFilter();
```

## setColor

setColor(color: common2D.Color) : void

设置画笔的颜色。

**系统能力：** SystemCapability.Graphics.Drawing

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型                                                 | 必填 | 说明             |
| ------ | ---------------------------------------------------- | ---- | ---------------- |
| color  | [common2D.Color](js-apis-graphics-common2D.md#color) | 是   | ARGB格式的颜色，每个颜色通道的值是0到255之间的整数。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types;3.Parameter verification failed. |

**示例：**

```ts
import { common2D, drawing } from '@kit.ArkGraphics2D';

const color : common2D.Color = { alpha: 255, red: 255, green: 0, blue: 0 };
const pen = new drawing.Pen();
pen.setColor(color);
```

## setColor<sup>12+</sup>

ArkTS-Dyn: setColor(alpha: number, red: number, green: number, blue: number): void

ArkTS-Sta: setColor(alpha: int, red: int, green: int, blue: int): void

设置画笔的颜色。性能优于[setColor](#setcolor)接口，推荐使用本接口。

**系统能力：** SystemCapability.Graphics.Drawing

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型    | 必填 | 说明                                                |
| ------ | ------ | ---- | -------------------------------------------------- |
| alpha  | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是   | ARGB格式颜色的透明度通道值，该参数是0到255之间的整数，传入范围内的浮点数会向下取整。 |
| red    | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是   | ARGB格式颜色的红色通道值，该参数是0到255之间的整数，传入范围内的浮点数会向下取整。   |
| green  | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是   | ARGB格式颜色的绿色通道值，该参数是0到255之间的整数，传入范围内的浮点数会向下取整。   |
| blue   | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是   | ARGB格式颜色的蓝色通道值，该参数是0到255之间的整数，传入范围内的浮点数会向下取整。   |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**示例：**

```ts
import { drawing } from '@kit.ArkGraphics2D';

const pen = new drawing.Pen();
pen.setColor(255, 255, 0, 0);
```

## setColor<sup>18+</sup>

ArkTS-Dyn: setColor(color: number): void

ArkTS-Sta: setColor(color: int): void

设置画笔的颜色。

**系统能力：** SystemCapability.Graphics.Drawing

**ArkTS-Dyn起始版本：** 18

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型                                 | 必填 | 说明                   |
| ------ | ------------------------------------ | ---- | ---------------------- |
| color  | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是   | 16进制ARGB格式的颜色。 |

**示例：**

```ts
import { drawing } from '@kit.ArkGraphics2D';

const pen = new drawing.Pen();
pen.setColor(0xffff0000);
```

## setColor4f<sup>20+</sup>

setColor4f(color4f: common2D.Color4f, colorSpace: colorSpaceManager.ColorSpaceManager | null): void

设置画笔的颜色以及标准色域，与[setColor](#setcolor)区别在于可以单独设置色域，适用于需要单独设置色域的场景。

**系统能力：** SystemCapability.Graphics.Drawing

**ArkTS-Dyn起始版本：** 20

**ArkTS-Sta起始版本：** 24

**参数：**

| 参数名 | 类型                                                 | 必填 | 说明             |
| ------ | ---------------------------------------------------- | ---- | ---------------- |
| color4f  | [common2D.Color4f](js-apis-graphics-common2D.md#color4f20) | 是   | ARGB格式的颜色，每个颜色通道的值是0.0-1.0之间的浮点数，大于1.0时，取1.0，小于0.0时，取0.0。|
| colorSpace  | [colorSpaceManager.ColorSpaceManager](js-apis-colorSpaceManager.md#colorspacemanager) \| null | 是   | 标准色域对象，null表示使用SRGB色域。|

**示例：**

```ts
import { common2D, drawing, colorSpaceManager } from "@kit.ArkGraphics2D";

const pen = new drawing.Pen();
let colorSpace = colorSpaceManager.create(colorSpaceManager.ColorSpace.BT2020_HLG);
let color4f:common2D.Color4f = {alpha:1.0, red:0.5, green:0.4, blue:0.7};
pen.setColor4f(color4f, colorSpace);
```

## getColor<sup>12+</sup>

ArkTS-Dyn: getColor(): common2D.Color

ArkTS-Sta: getColor(): common2D.Color | undefined

获取画笔的颜色。

**系统能力：** SystemCapability.Graphics.Drawing

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型           | 说明            |
| -------------- | -------------- |
| ArkTS-Dyn: [common2D.Color](js-apis-graphics-common2D.md#color)<br/>ArkTS-Sta: [common2D.Color](js-apis-graphics-common2D.md#color) \| undefined | 返回画笔的颜色。获取失败时返回undefined。 |

**示例：**

```ts
import { common2D, drawing } from '@kit.ArkGraphics2D';

const color : common2D.Color = { alpha: 255, red: 255, green: 0, blue: 0 };
const pen = new drawing.Pen();
pen.setColor(color);
let colorGet = pen.getColor();
```

## getColor4f<sup>20+</sup>

ArkTS-Dyn: getColor4f(): common2D.Color4f

ArkTS-Sta: getColor4f(): common2D.Color4f | undefined

获取画笔的颜色，与[getColor](#getcolor12)的区别在于返回值类型为浮点数，适用于需要浮点数类型的场景。

**系统能力：** SystemCapability.Graphics.Drawing

**ArkTS-Dyn起始版本：** 20

**ArkTS-Sta起始版本：** 24

**返回值：**

| 类型           | 说明            |
| -------------- | -------------- |
|ArkTS-Dyn: [common2D.Color4f](js-apis-graphics-common2D.md#color4f20)<br/>AtkTS-Sta:  [common2D.Color4f](js-apis-graphics-common2D.md#color4f20) \| undefined | 返回画笔的颜色。获取失败时返回undefined。 |

**示例：**

```ts
import { common2D, drawing, colorSpaceManager } from "@kit.ArkGraphics2D";

const pen = new drawing.Pen();
let colorSpace = colorSpaceManager.create(colorSpaceManager.ColorSpace.BT2020_HLG);
let color4f:common2D.Color4f = {alpha:1.0, red:0.5, green:0.4, blue:0.7};
pen.setColor4f(color4f, colorSpace);
let color = pen.getColor4f();
```

## getHexColor<sup>18+</sup>

ArkTS-Dyn: getHexColor(): number

ArkTS-Sta: getHexColor(): int

获取画笔的颜色。

**系统能力：** SystemCapability.Graphics.Drawing

**ArkTS-Dyn起始版本：** 18

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型           | 说明            |
| -------------- | -------------- |
| ArkTS-Dyn: number<br/>ArkTS-Sta: int | 返回画笔的颜色，以16进制ARGB格式的32位无符号整数表示。 |

**示例：**

```ts
import { common2D, drawing } from '@kit.ArkGraphics2D';

let color : common2D.Color = { alpha: 255, red: 255, green: 0, blue: 0 };
let pen = new drawing.Pen();
pen.setColor(color);
let hex_color = pen.getHexColor();
console.info('getHexColor: ', hex_color.toString(16));
```

## setStrokeWidth

ArkTS-Dyn: setStrokeWidth(width: number) : void

ArkTS-Sta: setStrokeWidth(width: double) : void

设置画笔的线宽。0线宽被视作特殊的极细线宽，在绘制时始终会被绘制为1像素，不随画布的缩放而改变；负数线宽在实际绘制时会被视作0线宽。

**系统能力：** SystemCapability.Graphics.Drawing

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型   | 必填 | 说明             |
| ------ | ------ | ---- | ---------------- |
| width  | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 是   | 表示线宽，该参数为浮点数。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**示例：**

```ts
import { drawing } from '@kit.ArkGraphics2D';

const pen = new drawing.Pen();
pen.setStrokeWidth(5.0);
```

## getWidth<sup>12+</sup>

ArkTS-Dyn: getWidth(): number

ArkTS-Sta: getWidth(): double

获取画笔的线宽属性，线宽描述了画笔绘制图形轮廓的宽度。

**系统能力：** SystemCapability.Graphics.Drawing

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型   | 说明            |
| ------ | -------------- |
| ArkTS-Dyn: number<br/>ArkTS-Sta: double | 返回画笔的线宽，单位为物理像素px。 |

**示例：**

```ts
import { drawing } from '@kit.ArkGraphics2D';

const pen = new drawing.Pen();
let width = pen.getWidth();
```

## setAntiAlias

setAntiAlias(aa: boolean) : void

设置画笔是否开启抗锯齿。开启后，可以使得图形的边缘在显示时更平滑。未调用此接口设置时，系统默认关闭抗锯齿。

**系统能力：** SystemCapability.Graphics.Drawing

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型    | 必填 | 说明                                              |
| ------ | ------- | ---- | ------------------------------------------------- |
| aa     | boolean | 是   | 表示是否开启抗锯齿。true表示开启，false表示关闭。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**示例：**

```ts
import { drawing } from '@kit.ArkGraphics2D';

const pen = new drawing.Pen();
pen.setAntiAlias(true);
```

## isAntiAlias<sup>12+</sup>

isAntiAlias(): boolean

获取画笔是否开启抗锯齿属性。

**系统能力：** SystemCapability.Graphics.Drawing

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型    | 说明                       |
| ------- | ------------------------- |
| boolean | 返回画笔是否开启抗锯齿属性，true表示开启，false表示关闭。 |

**示例：**

```ts
import { drawing } from '@kit.ArkGraphics2D';

const pen = new drawing.Pen();
let isAntiAlias = pen.isAntiAlias();
```

## setAlpha

ArkTS-Dyn: setAlpha(alpha: number) : void

ArkTS-Sta: setAlpha(alpha: int) : void

设置画笔的透明度。

**系统能力：** SystemCapability.Graphics.Drawing

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型   | 必填 | 说明                                     |
| ------ | ------ | ---- | ---------------------------------------- |
| alpha  | ArkTS-Dyn: number<br/>ArkTS-Sta: int | 是   | 用于表示透明度的[0, 255]区间内的整数值，传入浮点类型时向下取整。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types;3.Parameter verification failed. |

**示例：**

```ts
import { drawing } from '@kit.ArkGraphics2D';

const pen = new drawing.Pen();
pen.setAlpha(128);
```

## getAlpha<sup>12+</sup>

ArkTS-Dyn: getAlpha(): number

ArkTS-Sta: getAlpha(): int

获取画笔的透明度。

**系统能力：** SystemCapability.Graphics.Drawing

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型   | 说明              |
| ------ | ---------------- |
| ArkTS-Dyn: number<br/>ArkTS-Sta: int | 返回画笔的透明度，该返回值为0到255之间的整数。 |

**示例：**

```ts
import { drawing } from '@kit.ArkGraphics2D';

const pen = new drawing.Pen();
let alpha = pen.getAlpha();
```

## setColorFilter

setColorFilter(filter: ColorFilter | null) : void

给画笔添加额外的颜色滤波器。

**系统能力：** SystemCapability.Graphics.Drawing

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型                        | 必填 | 说明         |
| ------ | --------------------------- | ---- | ------------ |
| filter | ArkTS-Dyn: [ColorFilter](arkts-apis-graphics-drawing-ColorFilter.md)<br/>ArkTS-Sta: [ColorFilter](arkts-apis-graphics-drawing-ColorFilter.md) \| null | 是   | 颜色滤波器。null表示清空颜色滤波器。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**示例：**

ArkTS-Dyn示例：
```ts
import { drawing } from '@kit.ArkGraphics2D';

const pen = new drawing.Pen();
let colorFilter = drawing.ColorFilter.createLinearToSRGBGamma();
pen.setColorFilter(colorFilter);
```

ArkTS-Sta示例：
```ts
import { drawing } from '@kit.ArkGraphics2D';

const pen = new drawing.Pen();
let colorFilter = drawing.ColorFilter.createLinearToSRGBGamma();
if (colorFilter != undefined) {
  pen.setColorFilter(colorFilter!);
}
pen.setColorFilter(null);
```

## setMaskFilter<sup>12+</sup>

setMaskFilter(filter: MaskFilter | null): void

给画笔添加额外的蒙版滤镜。

**系统能力：** SystemCapability.Graphics.Drawing

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型                       | 必填 | 说明      |
| ------ | ------------------------- | ---- | --------- |
| filter | [MaskFilter](arkts-apis-graphics-drawing-MaskFilter.md) \| null | 是   | 蒙版滤镜。null表示清空蒙版滤镜。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**示例：**

ArkTS-Dyn示例：
```ts
import { RenderNode } from '@kit.ArkUI';
import { common2D, drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context : DrawContext) {
    const canvas = context.canvas;
    const pen = new drawing.Pen();
    pen.setStrokeWidth(5);
    pen.setColor({alpha: 255, red: 255, green: 0, blue: 0});
    let maskFilter = drawing.MaskFilter.createBlurMaskFilter(drawing.BlurType.OUTER, 10);
    pen.setMaskFilter(maskFilter);
  }
}
```

ArkTS-Sta示例：
```ts
import { RenderNode, DrawContext } from '@kit.ArkUI';
import { common2D, drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context : DrawContext) {
    const canvas = context.canvas;
    const pen = new drawing.Pen();
    pen.setStrokeWidth(5.0);
    pen.setColor({alpha: 255, red: 255, green: 0, blue: 0});
    let maskFilter = drawing.MaskFilter.createBlurMaskFilter(drawing.BlurType.OUTER, 10.0);
    if (maskFilter == undefined) {
      return;
    }
    pen.setMaskFilter(maskFilter);
    pen.setMaskFilter(null);
  }
}
```

## setPathEffect<sup>12+</sup>

setPathEffect(effect: PathEffect | null): void

设置画笔路径效果。

**系统能力：** SystemCapability.Graphics.Drawing

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名  | 类型                       | 必填 | 说明         |
| ------- | ------------------------- | ---- | ------------ |
| effect  | [PathEffect](arkts-apis-graphics-drawing-PathEffect.md) \| null | 是   | 路径效果对象。null表示清空路径效果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**示例：**

ArkTS-Dyn示例：
```ts
import { RenderNode } from '@kit.ArkUI';
import { common2D, drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context : DrawContext) {
    const canvas = context.canvas;
    const pen = new drawing.Pen();
    pen.setStrokeWidth(5);
    pen.setColor({alpha: 255, red: 255, green: 0, blue: 0});
    let pathEffect = drawing.PathEffect.createDashPathEffect([30, 10], 0);
    pen.setPathEffect(pathEffect);
  }
}
```

ArkTS-Sta示例：
```ts
import { RenderNode, DrawContext } from '@kit.ArkUI';
import { common2D, drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context : DrawContext) {
    const canvas = context.canvas;
    const pen = new drawing.Pen();
    pen.setStrokeWidth(5);
    pen.setColor({alpha: 255, red: 255, green: 0, blue: 0});
    let pathEffect = drawing.PathEffect.createDashPathEffect([30.0, 1.0], 0.0);
    if (pathEffect == undefined) {
      return;
    }
    pen.setPathEffect(pathEffect);
    pen.setPathEffect(null);
  }
}
```

## setShaderEffect<sup>12+</sup>

setShaderEffect(shaderEffect: ShaderEffect | null): void

设置画笔着色器效果。

**系统能力：** SystemCapability.Graphics.Drawing

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名  | 类型                       | 必填 | 说明         |
| ------- | ------------------------- | ---- | ------------ |
| shaderEffect  | [ShaderEffect](arkts-apis-graphics-drawing-ShaderEffect.md) \| null | 是   | 着色器对象。null表示清空着色器效果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**示例：**

ArkTS-Dyn示例：
```ts
import { drawing } from '@kit.ArkGraphics2D';

const pen = new drawing.Pen();
let shaderEffect = drawing.ShaderEffect.createLinearGradient({x: 100, y: 100}, {x: 300, y: 300}, [0xFF00FF00, 0xFFFF0000], drawing.TileMode.REPEAT);
pen.setShaderEffect(shaderEffect);
```

ArkTS-Sta示例：
```ts
import { drawing } from '@kit.ArkGraphics2D';

const pen = new drawing.Pen();
let shaderEffect = drawing.ShaderEffect.createLinearGradient({x: 100.0, y: 100.0}, {x: 300.0, y: 300.0}, [0xFF00FF00, 0xFFFF0000], drawing.TileMode.REPEAT);
if (shaderEffect != undefined) {
  pen.setShaderEffect(shaderEffect!);
}
pen.setShaderEffect(null);
```

## setShadowLayer<sup>12+</sup>

setShadowLayer(shadowLayer: ShadowLayer | null): void

设置画笔阴影层效果。当前仅在绘制文字时生效。

**系统能力：** SystemCapability.Graphics.Drawing

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名  | 类型                       | 必填 | 说明      |
| ------- | ------------------------- | ---- | --------- |
| shadowLayer  | [ShadowLayer](arkts-apis-graphics-drawing-ShadowLayer.md) \| null | 是   | 阴影层对象。null表示清空阴影层效果。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**示例：**

ArkTS-Dyn示例：
```ts
import { RenderNode } from '@kit.ArkUI';
import { common2D, drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context : DrawContext) {
    const canvas = context.canvas;
    let font = new drawing.Font();
    font.setSize(60);
    let textBlob = drawing.TextBlob.makeFromString("hello", font, drawing.TextEncoding.TEXT_ENCODING_UTF8);
    let pen = new drawing.Pen();
    pen.setStrokeWidth(2.0);
    let pen_color : common2D.Color = {alpha: 0xFF, red: 0xFF, green: 0x00, blue: 0x00};
    pen.setColor(pen_color);
    canvas.attachPen(pen);
    canvas.drawTextBlob(textBlob, 100, 100);
    canvas.detachPen();
    let color : common2D.Color = {alpha: 0xFF, red: 0x00, green: 0xFF, blue: 0x00};
    let shadowLayer = drawing.ShadowLayer.create(3, -3, 3, color);
    pen.setShadowLayer(shadowLayer);
    canvas.attachPen(pen);
    canvas.drawTextBlob(textBlob, 100, 200);
    canvas.detachPen();
  }
}
```

ArkTS-Sta示例：
```ts
import { RenderNode, DrawContext } from '@kit.ArkUI';
import { common2D, drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context : DrawContext) {
    const canvas = context.canvas;
    let font = new drawing.Font();
    font.setSize(60.0);
    let textBlob = drawing.TextBlob.makeFromString("hello", font, drawing.TextEncoding.TEXT_ENCODING_UTF8);
    if (textBlob == undefined) {
      return;
    }
    let pen = new drawing.Pen();
    pen.setStrokeWidth(2.0);
    let pen_color : common2D.Color = {alpha: 0xFF, red: 0xFF, green: 0x00, blue: 0x00};
    pen.setColor(pen_color);
    canvas.attachPen(pen);
    canvas.drawTextBlob(textBlob, 100.0, 100.0);
    canvas.detachPen();
    let color : common2D.Color = {alpha: 0xFF, red: 0x00, green: 0xFF, blue: 0x00};
    let shadowLayer = drawing.ShadowLayer.create(3.0, -3.0, 3.0, color);
    if (shadowLayer == undefined) {
      return;
    }
    pen.setShadowLayer(shadowLayer);
    canvas.attachPen(pen);
    canvas.drawTextBlob(textBlob, 100.0, 200.0);
    canvas.detachPen();
    pen.setShadowLayer(null);
    canvas.attachPen(pen);
    canvas.drawTextBlob(textBlob, 100, 200);
    canvas.detachPen();
  }
}
```

## setBlendMode

setBlendMode(mode: BlendMode) : void

设置画笔的混合模式。

**系统能力：** SystemCapability.Graphics.Drawing

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型                    | 必填 | 说明             |
| ------ | ----------------------- | ---- | ---------------- |
| mode   | [BlendMode](arkts-apis-graphics-drawing-e.md#blendmode) | 是   | 颜色的混合模式。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types;3.Parameter verification failed. |

**示例：**

```ts
import { drawing } from '@kit.ArkGraphics2D';

const pen = new drawing.Pen();
pen.setBlendMode(drawing.BlendMode.SRC);
```

## setJoinStyle<sup>12+</sup>

setJoinStyle(style: JoinStyle): void

设置画笔绘制转角的样式。未调用此接口设置时，系统默认的转角样式为MITER_JOIN。

**系统能力：** SystemCapability.Graphics.Drawing

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型                     | 必填 | 说明             |
| ------ | ----------------------- | ---- | --------------- |
| style  | [JoinStyle](arkts-apis-graphics-drawing-e.md#joinstyle12) | 是   | 折线转角样式。     |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types;3.Parameter verification failed. |

**示例：**

ArkTS-Dyn示例：
```ts
import { RenderNode } from '@kit.ArkUI';
import { common2D, drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context : DrawContext) {
    const canvas = context.canvas;
    const pen = new drawing.Pen();
    pen.setStrokeWidth(5);
    pen.setColor({alpha: 255, red: 255, green: 0, blue: 0});
    pen.setJoinStyle(drawing.JoinStyle.ROUND_JOIN);
  }
}
```

ArkTS-Sta示例：
```ts
import { RenderNode, DrawContext } from '@kit.ArkUI';
import { common2D, drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context : DrawContext) {
    const canvas = context.canvas;
    const pen = new drawing.Pen();
    pen.setStrokeWidth(5.0);
    pen.setColor({alpha: 255, red: 255, green: 0, blue: 0});
    pen.setJoinStyle(drawing.JoinStyle.ROUND_JOIN);
  }
}
```

## getJoinStyle<sup>12+</sup>

getJoinStyle(): JoinStyle

获取画笔绘制转角的样式。

**系统能力：** SystemCapability.Graphics.Drawing

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型          | 说明                    |
| ------------- | ---------------------- |
| JoinStyle | 返回折线转角的样式。         |

**示例：**

ArkTS-Dyn示例：
```ts
import { RenderNode } from '@kit.ArkUI';
import { common2D, drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context : DrawContext) {
    const canvas = context.canvas;
    const pen = new drawing.Pen();
    pen.setStrokeWidth(5);
    pen.setColor({alpha: 255, red: 255, green: 0, blue: 0});
    pen.setJoinStyle(drawing.JoinStyle.ROUND_JOIN);
    let joinStyle = pen.getJoinStyle();
  }
}
```

ArkTS-Sta示例：
```ts
import { RenderNode, DrawContext } from '@kit.ArkUI';
import { common2D, drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context : DrawContext) {
    const canvas = context.canvas;
    const pen = new drawing.Pen();
    pen.setStrokeWidth(5.0);
    pen.setColor({alpha: 255, red: 255, green: 0, blue: 0});
    pen.setJoinStyle(drawing.JoinStyle.ROUND_JOIN);
    let joinStyle = pen.getJoinStyle();
  }
}
```

## setCapStyle<sup>12+</sup>

setCapStyle(style: CapStyle): void

设置画笔的线帽样式。未调用此接口设置时，系统默认的线帽样式为FLAT_CAP。

**系统能力：** SystemCapability.Graphics.Drawing

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型                     | 必填 | 说明                   |
| ------ | ----------------------- | ---- | --------------------- |
| style  | [CapStyle](arkts-apis-graphics-drawing-e.md#capstyle12)   | 是   | 描述画笔的线帽样式。    |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types;3.Parameter verification failed. |

**示例：**

ArkTS-Dyn示例：
```ts
import { RenderNode } from '@kit.ArkUI';
import { common2D, drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context : DrawContext) {
    const canvas = context.canvas;
    const pen = new drawing.Pen();
    pen.setStrokeWidth(5);
    pen.setColor({alpha: 255, red: 255, green: 0, blue: 0});
    pen.setCapStyle(drawing.CapStyle.SQUARE_CAP);
  }
}
```

ArkTS-Sta示例：
```ts
import { RenderNode, DrawContext } from '@kit.ArkUI';
import { common2D, drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context : DrawContext) {
    const canvas = context.canvas;
    const pen = new drawing.Pen();
    pen.setStrokeWidth(5);
    pen.setColor({alpha: 255, red: 255, green: 0, blue: 0});
    pen.setCapStyle(drawing.CapStyle.SQUARE_CAP);
  }
}
```

## getCapStyle<sup>12+</sup>

getCapStyle(): CapStyle

获取画笔的线帽样式。

**系统能力：** SystemCapability.Graphics.Drawing

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型         | 说明                |
| ------------ | ------------------ |
| CapStyle     | 返回画笔的线帽样式。 |

**示例：**

ArkTS-Dyn示例：
```ts
import { RenderNode } from '@kit.ArkUI';
import { common2D, drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context : DrawContext) {
    const canvas = context.canvas;
    const pen = new drawing.Pen();
    pen.setStrokeWidth(5);
    pen.setColor({alpha: 255, red: 255, green: 0, blue: 0});
    pen.setCapStyle(drawing.CapStyle.SQUARE_CAP);
    let capStyle = pen.getCapStyle();
  }
}
```

ArkTS-Sta示例：
```ts
import { RenderNode, DrawContext } from '@kit.ArkUI';
import { common2D, drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context : DrawContext) {
    const canvas = context.canvas;
    const pen = new drawing.Pen();
    pen.setStrokeWidth(5.0);
    pen.setColor({alpha: 255, red: 255, green: 0, blue: 0});
    pen.setCapStyle(drawing.CapStyle.SQUARE_CAP);
    let capStyle = pen.getCapStyle();
  }
}
```

## setDither

setDither(dither: boolean) : void

开启画笔的抖动绘制效果。抖动绘制可以使得绘制出的颜色更加真实。

**系统能力：** SystemCapability.Graphics.Drawing

**ArkTS-Dyn起始版本：** 11

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名 | 类型    | 必填 | 说明                                                      |
| ------ | ------- | ---- | --------------------------------------------------------- |
| dither | boolean | 是   | 是否开启画笔的抖动绘制效果。true表示开启，false表示关闭。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**示例：**

```ts
import { drawing } from '@kit.ArkGraphics2D';

const pen = new drawing.Pen();
pen.setDither(true);
```

## getFillPath<sup>12+</sup>

getFillPath(src: Path, dst: Path): boolean

获取使用画笔绘制的源路径轮廓，并用目标路径表示。

**系统能力：** SystemCapability.Graphics.Drawing

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名   | 类型                                         | 必填 | 说明                            |
| -------- | -------------------------------------------- | ---- | ------------------------------- |
| src | [Path](arkts-apis-graphics-drawing-Path.md) | 是   | 源路径对象。                 |
| dst     | [Path](arkts-apis-graphics-drawing-Path.md)                | 是   | 目标路径对象。 |

**返回值：**

| 类型                  | 说明           |
| --------------------- | -------------- |
| boolean | 返回获取源路径轮廓是否成功，true表示成功，false表示失败。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**示例：**

ArkTS-Dyn示例：
```ts
import { drawing } from '@kit.ArkGraphics2D';

let pen = new drawing.Pen();
let pathSrc: drawing.Path = new drawing.Path();
let pathDst: drawing.Path = new drawing.Path();
pathSrc.moveTo(0, 0);
pathSrc.lineTo(700, 700);
let value = pen.getFillPath(pathSrc, pathDst);
```

ArkTS-Sta示例：
```ts
import { drawing } from '@kit.ArkGraphics2D';

let pen = new drawing.Pen();
let pathSrc: drawing.Path = new drawing.Path();
let pathDst: drawing.Path = new drawing.Path();
pathSrc.moveTo(0.0, 0.0);
pathSrc.lineTo(700.0, 700.0);
let value = pen.getFillPath(pathSrc, pathDst);
```

## reset<sup>12+</sup>

reset(): void

重置当前画笔为初始状态。

**系统能力：** SystemCapability.Graphics.Drawing

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 23

**示例：**

```ts
import { drawing } from '@kit.ArkGraphics2D';

const pen = new drawing.Pen();
pen.reset();
```