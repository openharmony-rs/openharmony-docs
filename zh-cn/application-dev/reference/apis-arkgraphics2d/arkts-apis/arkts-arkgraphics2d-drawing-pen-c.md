# Pen

画笔对象，用于描述所绘制图形形状的轮廓信息，支持设置颜色、线宽、抗锯齿、透明度、混合模式、转角样式、线帽样式，以及颜色滤波器、蒙版滤波器、路径效果、着色器、阴影层等绘制效果。

> **说明：**
> 
> - 本模块使用屏幕物理像素单位px。
> 
> - 本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。

**起始版本：** 11

**系统能力：** SystemCapability.Graphics.Drawing

## 导入模块

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';
```

## constructor

```TypeScript
constructor()
```

构造一个新的画笔对象。

**起始版本：** 12

**系统能力：** SystemCapability.Graphics.Drawing

**示例**

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

const brush = new drawing.Brush();
```

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

let matrix = new drawing.Matrix();
```

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

let path: drawing.Path = new drawing.Path();
```

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

const pen = new drawing.Pen();
```

```TypeScript
import { RenderNode, DrawContext } from '@kit.ArkUI';
import { drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context: DrawContext) {
    let samplingOptions = new drawing.SamplingOptions();
  }
}
```

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';
let typefaceArgument = new drawing.TypefaceArguments();
```

## constructor

```TypeScript
constructor(pen: Pen)
```

复制构造一个新的画笔对象。

**起始版本：** 12

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pen | Pen | 是 | 待复制的画笔对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types. |

**示例**

```TypeScript
import { common2D, drawing } from '@kit.ArkGraphics2D';

const pen = new drawing.Pen();
const penColor: common2D.Color = { alpha: 255, red: 0, green: 255, blue: 0 };
pen.setColor(penColor);
pen.setStrokeWidth(10);
const newPen = new drawing.Pen(pen);
```

## getAlpha

```TypeScript
getAlpha(): number
```

获取画笔的透明度。

**起始版本：** 12

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回画笔的透明度，该返回值为0到255之间的整数。 |

**示例**

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

const brush = new drawing.Brush();
let alpha = brush.getAlpha();
```

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

const pen = new drawing.Pen();
let alpha = pen.getAlpha();
```

## getCapStyle

```TypeScript
getCapStyle(): CapStyle
```

获取画笔的线帽样式。

**起始版本：** 12

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [CapStyle](arkts-arkgraphics2d-drawing-capstyle-e.md) | 返回画笔的线帽样式。 |

**示例**

```TypeScript
import { RenderNode } from '@kit.ArkUI';
import { common2D, drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context : DrawContext) {
    const canvas = context.canvas;
    const pen = new drawing.Pen();
    pen.setStrokeWidth(5);
    pen.setColor({alpha: 255, red: 255, green: 0, blue: 0});
    pen.setCapStyle(drawing.CapStyle.SQUARE_CAP);
    pen.getCapStyle();
  }
}
```

## getColor

```TypeScript
getColor(): common2D.Color
```

获取画笔的颜色。

**起始版本：** 12

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| common2D.Color | 返回画笔当前设置的颜色。 |

**示例**

```TypeScript
import { common2D, drawing } from '@kit.ArkGraphics2D';

const color : common2D.Color = { alpha: 255, red: 255, green: 0, blue: 0 };
const brush = new drawing.Brush();
brush.setColor(color);
let currentColor = brush.getColor();
```

```TypeScript
import { common2D, drawing } from '@kit.ArkGraphics2D';

const color : common2D.Color = { alpha: 255, red: 255, green: 0, blue: 0 };
const pen = new drawing.Pen();
pen.setColor(color);
let colorGet = pen.getColor();
```

## getColor4f

```TypeScript
getColor4f(): common2D.Color4f
```

获取画笔的颜色，与[getColor](#getcolor)的区别在于返回值类型为 [common2D.Color4f](arkts-arkgraphics2d-common2d-color4f-i.md)，颜色通道值为浮点数，适用于需要浮点数类型的场景。

**起始版本：** 20

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| common2D.Color4f | 返回画笔当前设置的颜色，为ARGB格式的浮点数表示，每个颜色通道的取值范围为[0.0, 1.0]。 |

**示例**

```TypeScript
import { common2D, drawing, colorSpaceManager } from '@kit.ArkGraphics2D';

const brush = new drawing.Brush();
let colorSpace = colorSpaceManager.create(colorSpaceManager.ColorSpace.BT2020_HLG);
let color4f: common2D.Color4f = { alpha: 1, red: 0.5, green: 0.4, blue: 0.7 };
brush.setColor4f(color4f, colorSpace);
let color = brush.getColor4f();
```

```TypeScript
import { common2D, drawing, colorSpaceManager } from "@kit.ArkGraphics2D";

const pen = new drawing.Pen();
let colorSpace = colorSpaceManager.create(colorSpaceManager.ColorSpace.BT2020_HLG);
let color4f: common2D.Color4f = {alpha: 1, red: 0.5, green: 0.4, blue: 0.7};
pen.setColor4f(color4f, colorSpace);
let color = pen.getColor4f();
```

## getColorFilter

```TypeScript
getColorFilter(): ColorFilter
```

获取画笔的颜色滤波器。

**起始版本：** 12

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ColorFilter | 返回画笔当前设置的颜色滤波器，可用于查询当前画笔的颜色过滤效果。 |

**示例**

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

let brush = new drawing.Brush();
let colorFilter = drawing.ColorFilter.createSRGBGammaToLinear();
brush.setColorFilter(colorFilter);
let currentFilter = brush.getColorFilter();
```

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

let pen = new drawing.Pen();
let colorFilter = drawing.ColorFilter.createLumaColorFilter();
pen.setColorFilter(colorFilter);
let filter = pen.getColorFilter();
```

## getFillPath

```TypeScript
getFillPath(src: Path, dst: Path): boolean
```

获取使用画笔绘制的源路径轮廓，并用目标路径表示。

**起始版本：** 12

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | Path | 是 | 待提取轮廓的源路径对象。 |
| dst | Path | 是 | 目标路径对象，用于存储根据画笔属性从src路径计算得到的轮廓结果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回获取源路径轮廓是否成功，true表示成功，false表示失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types. |

**示例**

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

let pen = new drawing.Pen();
let pathSrc: drawing.Path = new drawing.Path();
let pathDst: drawing.Path = new drawing.Path();
pathSrc.moveTo(0, 0);
pathSrc.lineTo(700, 700);
let value = pen.getFillPath(pathSrc, pathDst);
```

## getHexColor

```TypeScript
getHexColor(): number
```

获取画笔的颜色。

**起始版本：** 18

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回画笔的颜色，以16进制ARGB格式的32位无符号整数表示。 |

**示例**

```TypeScript
import { common2D, drawing } from '@kit.ArkGraphics2D';

let color : common2D.Color = { alpha: 255, red: 255, green: 0, blue: 0 };
let brush = new drawing.Brush();
brush.setColor(color);
let hexColor: number = brush.getHexColor();
console.info('getHexColor: ', hexColor.toString(16));
```

```TypeScript
import { common2D, drawing } from '@kit.ArkGraphics2D';

let color : common2D.Color = { alpha: 255, red: 255, green: 0, blue: 0 };
let pen = new drawing.Pen();
pen.setColor(color);
let hexColor: number = pen.getHexColor();
console.info('getHexColor: ', hexColor.toString(16));
```

## getJoinStyle

```TypeScript
getJoinStyle(): JoinStyle
```

获取画笔绘制转角的样式。

**起始版本：** 12

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [JoinStyle](arkts-arkgraphics2d-drawing-joinstyle-e.md) | 返回折线转角的样式。 |

**示例**

```TypeScript
import { RenderNode } from '@kit.ArkUI';
import { common2D, drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context : DrawContext) {
    const canvas = context.canvas;
    const pen = new drawing.Pen();
    pen.setStrokeWidth(5);
    pen.setColor({alpha: 255, red: 255, green: 0, blue: 0});
    pen.setJoinStyle(drawing.JoinStyle.ROUND_JOIN);
    pen.getJoinStyle();
  }
}
```

## getMiterLimit

```TypeScript
getMiterLimit(): number
```

获取折线尖角长度与线宽的最大比值。

**起始版本：** 12

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回折线尖角长度与线宽的最大比值。 |

**示例**

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

const pen = new drawing.Pen();
let miter = pen.getMiterLimit();
```

## getWidth

```TypeScript
getWidth(): number
```

获取画笔的线宽属性，线宽描述了画笔绘制图形轮廓的宽度。

**起始版本：** 12

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回画笔的线宽，单位为物理像素px。 |

**示例**

```TypeScript
import { RenderNode } from '@kit.ArkUI';
import { drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context : DrawContext) {
    const canvas = context.canvas;
    let width = canvas.getWidth();
    console.info('get canvas width:' + width);
  }
}
```

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

const pen = new drawing.Pen();
let width = pen.getWidth();
```

## isAntiAlias

```TypeScript
isAntiAlias(): boolean
```

获取画笔是否开启抗锯齿属性。

**起始版本：** 12

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回画笔是否开启抗锯齿属性，true表示开启，false表示关闭。 |

**示例**

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

const brush = new drawing.Brush();
let isAntiAlias = brush.isAntiAlias();
```

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

const pen = new drawing.Pen();
let isAntiAlias = pen.isAntiAlias();
```

## reset

```TypeScript
reset(): void
```

重置当前画笔为初始状态。

**起始版本：** 12

**系统能力：** SystemCapability.Graphics.Drawing

**示例**

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

const brush = new drawing.Brush();
brush.reset();
```

```TypeScript
import { drawing } from "@kit.ArkGraphics2D";

let matrix = new drawing.Matrix();
matrix.postScale(2, 3, 4, 5);
matrix.reset();
console.info("matrix= "+matrix.getAll().toString());
```

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

let path = new drawing.Path();
path.moveTo(10, 10);
path.cubicTo(10, 10, 10, 10, 15, 15);
path.reset();
```

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

const pen = new drawing.Pen();
pen.reset();
```

## setAlpha

```TypeScript
setAlpha(alpha: number): void
```

设置画笔的透明度。

**起始版本：** 11

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| alpha | number | 是 | 表示透明度，取值范围为[0, 255]，传入浮点类型时向下取整。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

const brush = new drawing.Brush();
brush.setAlpha(128);
```

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

const pen = new drawing.Pen();
pen.setAlpha(128);
```

## setAntiAlias

```TypeScript
setAntiAlias(aa: boolean): void
```

设置画笔是否开启抗锯齿。开启后，使图形边缘在显示时更平滑。未调用此接口设置时，系统默认关闭抗锯齿。

**起始版本：** 11

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| aa | boolean | 是 | 表示是否开启抗锯齿。true表示开启，false表示关闭。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types. |

**示例**

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

const brush = new drawing.Brush();
brush.setAntiAlias(true);
```

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

const pen = new drawing.Pen();
pen.setAntiAlias(true);
```

## setBlendMode

```TypeScript
setBlendMode(mode: BlendMode): void
```

设置画笔的混合模式。

**起始版本：** 11

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | BlendMode | 是 | 颜色的混合模式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

const brush = new drawing.Brush();
brush.setBlendMode(drawing.BlendMode.SRC);
```

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

const pen = new drawing.Pen();
pen.setBlendMode(drawing.BlendMode.SRC);
```

## setCapStyle

```TypeScript
setCapStyle(style: CapStyle): void
```

设置画笔的线帽样式。未调用此接口设置时，系统默认的线帽样式为FLAT_CAP。

**起始版本：** 12

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [CapStyle](arkts-arkgraphics2d-drawing-capstyle-e.md) | 是 | 描述画笔的线帽样式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

```TypeScript
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

## setColor

```TypeScript
setColor(color: common2D.Color): void
```

设置画笔的颜色。

**起始版本：** 11

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | common2D.Color | 是 | ARGB格式的颜色，每个颜色通道的值是0到255之间的整数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

```TypeScript
import { common2D, drawing } from '@kit.ArkGraphics2D';

const color : common2D.Color = { alpha: 255, red: 255, green: 0, blue: 0 };
const brush = new drawing.Brush();
brush.setColor(color);
```

```TypeScript
import { common2D, drawing } from '@kit.ArkGraphics2D';

const color : common2D.Color = { alpha: 255, red: 255, green: 0, blue: 0 };
const pen = new drawing.Pen();
pen.setColor(color);
```

## setColor

```TypeScript
setColor(alpha: number, red: number, green: number, blue: number): void
```

设置画笔的颜色。性能优于[setColor](#setcolor)接口，推荐使用本接口。

**起始版本：** 12

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| alpha | number | 是 | ARGB格式颜色的透明度通道值，该参数取值范围是[0, 255]，传入范围内的浮点数会向下取整，超出范围的值会被截断到0或255。 |
| red | number | 是 | ARGB格式颜色的红色通道值，该参数取值范围是[0, 255]，传入范围内的浮点数会向下取整，超出范围的值会被截断到0或255。 |
| green | number | 是 | ARGB格式颜色的绿色通道值，该参数取值范围是[0, 255]，传入范围内的浮点数会向下取整，超出范围的值会被截断到0或255。 |
| blue | number | 是 | ARGB格式颜色的蓝色通道值，该参数取值范围是[0, 255]，传入范围内的浮点数会向下取整，超出范围的值会被截断到0或255。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types. |

**示例**

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

const brush = new drawing.Brush();
brush.setColor(255, 255, 0, 0);
```

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

const pen = new drawing.Pen();
pen.setColor(255, 255, 0, 0);
```

## setColor

```TypeScript
setColor(color: number): void
```

设置画笔的颜色。

**起始版本：** 18

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | number | 是 | 16进制ARGB格式的颜色，格式为0xAARRGGBB，其中AA表示透明度通道，RR表示红色通道，GG表示绿色通道，BB表示蓝色通道，各通道取值范围为00-FF，取值范围为 [0x00000000, 0xFFFFFFFF]。超出有效范围的值会被截断处理。 |

**示例**

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

const brush = new drawing.Brush();
brush.setColor(0xffff0000);
```

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

const pen = new drawing.Pen();
pen.setColor(0xffff0000);
```

## setColor4f

```TypeScript
setColor4f(color4f: common2D.Color4f, colorSpace: colorSpaceManager.ColorSpaceManager | null): void
```

设置画笔的颜色以及标准色域，与[setColor](#setcolor)的区别在于可以单独设置色域。

**起始版本：** 20

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color4f | common2D.Color4f | 是 | ARGB格式的颜色，浮点数，每个颜色通道值的范围为[0.0, 1.0]，超出范围的值会被截断到0.0或1.0。 |
| colorSpace | colorSpaceManager.ColorSpaceManager \| null | 是 | 标准色域对象，null表示使用SRGB色域。 |

**示例**

```TypeScript
import { common2D, drawing, colorSpaceManager } from '@kit.ArkGraphics2D';

const brush = new drawing.Brush();
let colorSpace = colorSpaceManager.create(colorSpaceManager.ColorSpace.BT2020_HLG);
let color4f: common2D.Color4f = { alpha: 1, red: 0.5, green: 0.4, blue: 0.7 };
brush.setColor4f(color4f, colorSpace);
```

```TypeScript
import { common2D, drawing, colorSpaceManager } from "@kit.ArkGraphics2D";

const pen = new drawing.Pen();
let colorSpace = colorSpaceManager.create(colorSpaceManager.ColorSpace.BT2020_HLG);
let color4f: common2D.Color4f = {alpha: 1, red: 0.5, green: 0.4, blue: 0.7};
pen.setColor4f(color4f, colorSpace);
```

## setColorFilter

```TypeScript
setColorFilter(filter: ColorFilter | null): void
```

给画笔添加额外的颜色滤波器。

**起始版本：** 11

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filter | ColorFilter \| null | 是 | 颜色滤波器。null表示清空颜色滤波器。<br>**起始版本：** 20 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types. |

**示例**

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

const brush = new drawing.Brush();
let colorFilter = drawing.ColorFilter.createLinearToSRGBGamma();
brush.setColorFilter(colorFilter);
```

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

const pen = new drawing.Pen();
let colorFilter = drawing.ColorFilter.createLinearToSRGBGamma();
pen.setColorFilter(colorFilter);
```

## setDither

```TypeScript
setDither(dither: boolean): void
```

设置画笔是否开启抖动绘制效果。抖动绘制使颜色更真实。

**起始版本：** 11

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dither | boolean | 是 | 是否开启画笔的抖动绘制效果。true表示开启，false表示关闭。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types. |

**示例**

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

const pen = new drawing.Pen();
pen.setDither(true);
```

## setImageFilter

```TypeScript
setImageFilter(filter: ImageFilter | null): void
```

设置画笔的图像滤波器。

**起始版本：** 12

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filter | [ImageFilter](arkts-arkgraphics2d-drawing-imagefilter-c.md) \| null | 是 | 图像滤波器，null表示清空画笔的图像滤波器效果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types. |

**示例**

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

let brush = new drawing.Brush();
let imageFilter = drawing.ImageFilter.createBlurImageFilter(5, 10, drawing.TileMode.DECAL);
brush.setImageFilter(imageFilter);
brush.setImageFilter(null);
```

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

let colorfilter = drawing.ColorFilter.createSRGBGammaToLinear();
let imgFilter = drawing.ImageFilter.createFromColorFilter(colorfilter);
let pen = new drawing.Pen();
pen.setImageFilter(imgFilter);
pen.setImageFilter(null);
```

## setJoinStyle

```TypeScript
setJoinStyle(style: JoinStyle): void
```

设置画笔绘制转角的样式。未调用此接口设置时，系统默认的转角样式为MITER_JOIN。

**起始版本：** 12

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| style | [JoinStyle](arkts-arkgraphics2d-drawing-joinstyle-e.md) | 是 | 折线转角样式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

```TypeScript
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

## setMaskFilter

```TypeScript
setMaskFilter(filter: MaskFilter | null): void
```

给画笔添加额外的蒙版滤镜。

**起始版本：** 12

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filter | [MaskFilter](arkts-arkgraphics2d-drawing-maskfilter-c.md) \| null | 是 | 蒙版滤镜。null表示清空蒙版滤镜。<br>**起始版本：** 20 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types. |

**示例**

```TypeScript
import { RenderNode, DrawContext } from '@kit.ArkUI';
import { drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context : DrawContext) {
    const brush = new drawing.Brush();
    let maskFilter = drawing.MaskFilter.createBlurMaskFilter(drawing.BlurType.OUTER, 10);
    brush.setMaskFilter(maskFilter);
  }
}
```

```TypeScript
import { RenderNode } from '@kit.ArkUI';
import { common2D, drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context : DrawContext) {
    const pen = new drawing.Pen();
    pen.setStrokeWidth(5);
    pen.setColor({alpha: 255, red: 255, green: 0, blue: 0});
    let maskFilter = drawing.MaskFilter.createBlurMaskFilter(drawing.BlurType.OUTER, 10);
    pen.setMaskFilter(maskFilter);
  }
}
```

## setMiterLimit

```TypeScript
setMiterLimit(miter: number): void
```

设置折线尖角长度与线宽的最大比值。当画笔绘制一条折线，并且[JoinStyle](arkts-arkgraphics2d-drawing-joinstyle-e.md)为MITER_JOIN时，若尖角长度与线宽的比值大于该最大比值，则该转角使用BEVEL_JOIN 绘制。

**起始版本：** 12

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| miter | number | 是 | 折线尖角长度与线宽的最大比值，负数在绘制时会被视作4.0处理，非负数按实际传入值生效，该参数为浮点数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types. |

**示例**

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

const pen = new drawing.Pen();
pen.setMiterLimit(5);
```

## setPathEffect

```TypeScript
setPathEffect(effect: PathEffect | null): void
```

设置画笔路径效果。

**起始版本：** 12

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| effect | [PathEffect](arkts-arkgraphics2d-drawing-patheffect-c.md) \| null | 是 | 路径效果对象，用于设置虚线、转角等路径绘制样式。null表示清空路径效果。<br>**起始版本：** 20 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types. |

**示例**

```TypeScript
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

## setShaderEffect

```TypeScript
setShaderEffect(shaderEffect: ShaderEffect | null): void
```

设置画笔着色器效果。

**起始版本：** 12

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| shaderEffect | [ShaderEffect](arkts-arkgraphics2d-drawing-shadereffect-c.md) \| null | 是 | 着色器效果对象。null表示清空着色器效果。<br>**起始版本：** 20 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types. |

**示例**

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

const brush = new drawing.Brush();
let shaderEffect = drawing.ShaderEffect.createLinearGradient({x: 100, y: 100}, {x: 300, y: 300}, [0xFF00FF00, 0xFFFF0000], drawing.TileMode.REPEAT);
brush.setShaderEffect(shaderEffect);
```

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

const pen = new drawing.Pen();
let shaderEffect = drawing.ShaderEffect.createLinearGradient({x: 100, y: 100}, {x: 300, y: 300}, [0xFF00FF00, 0xFFFF0000], drawing.TileMode.REPEAT);
pen.setShaderEffect(shaderEffect);
```

## setShadowLayer

```TypeScript
setShadowLayer(shadowLayer: ShadowLayer | null): void
```

设置画笔阴影层效果。当前仅在绘制文字时生效。

**起始版本：** 12

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| shadowLayer | [ShadowLayer](arkts-arkgraphics2d-drawing-shadowlayer-c.md) \| null | 是 | 阴影层对象。null表示清空阴影层效果。<br>**起始版本：** 20 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types. |

**示例**

```TypeScript
import { RenderNode, DrawContext } from '@kit.ArkUI';
import { common2D, drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context : DrawContext) {
    const canvas = context.canvas;
    let font = new drawing.Font();
    font.setSize(60);

    let textBlob = drawing.TextBlob.makeFromString('hello', font, drawing.TextEncoding.TEXT_ENCODING_UTF8);
    let pen = new drawing.Pen();
    pen.setStrokeWidth(2.0);

    let penColor : common2D.Color = {alpha: 0xFF, red: 0xFF, green: 0x00, blue: 0x00};
    pen.setColor(penColor);
    canvas.attachPen(pen);
    canvas.drawTextBlob(textBlob, 100, 100);
    canvas.detachPen();

    let color : common2D.Color = {alpha: 0xFF, red: 0x00, green: 0xFF, blue: 0x00};
    let shadowLayer = drawing.ShadowLayer.create(3, -3, 3, color);
    pen.setShadowLayer(shadowLayer);
    canvas.attachPen(pen);
    canvas.drawTextBlob(textBlob, 100, 200);
    canvas.detachPen();

    let brush = new drawing.Brush();
    let brushColor : common2D.Color = {alpha: 0xFF, red: 0xFF, green: 0x00, blue: 0x00};
    brush.setColor(brushColor);
    canvas.attachBrush(brush);
    canvas.drawTextBlob(textBlob, 300, 100);
    canvas.detachBrush();

    brush.setShadowLayer(shadowLayer);
    canvas.attachBrush(brush);
    canvas.drawTextBlob(textBlob, 300, 200);
    canvas.detachBrush();
  }
}
```

```TypeScript
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

## setStrokeWidth

```TypeScript
setStrokeWidth(width: number): void
```

设置画笔的线宽。0线宽被视作特殊的极细线宽，在绘制时始终会被绘制为1像素，不随画布的缩放而改变；负数线宽在实际绘制时会被视作0线宽。

**起始版本：** 11

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| width | number | 是 | 表示线宽，该参数为浮点数，单位为物理像素px。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types. |

**示例**

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

const pen = new drawing.Pen();
pen.setStrokeWidth(5);
```
