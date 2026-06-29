# Class (ShadowLayer)

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @dreamyhhh-->
<!--Designer: @wanyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->

阴影层对象，通过设置模糊半径、偏移量和颜色，可为图形、文本等绘制内容添加阴影渲染效果，适用于需要实现阴影、发光等视觉特效的场景。

> **说明：**
>
> - 本模块首批接口从API version 11开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 本Class首批接口从API version 12开始支持。
>
> - 本模块使用屏幕物理像素单位px。
>
> - 本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。

## 导入模块

```ts
import { drawing } from '@kit.ArkGraphics2D';
```

## create<sup>12+</sup>

static create(blurRadius: number, x: number, y: number, color: common2D.Color): ShadowLayer

创建阴影层对象。适用于为图形、文本等绘制内容添加阴影、发光等视觉特效的场景。

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名     | 类型      | 必填 | 说明                                 |
| ---------- | -------- | ---- | ----------------------------------- |
| blurRadius  | number   | 是   | 阴影的半径，必须为大于0的浮点数。单位为物理像素px。     |
| x           | number   | 是   | x轴上的偏移量，该参数为浮点数。单位为物理像素px。        |
| y           | number   | 是   | y轴上的偏移量，该参数为浮点数。单位为物理像素px。        |
| color       | [common2D.Color](js-apis-graphics-common2D.md#color) | 是   | ARGB格式的颜色。每个颜色通道的值是[0, 255]的整数。 |

**返回值：**

| 类型                        | 说明                  |
| --------------------------- | -------------------- |
| [ShadowLayer](arkts-apis-graphics-drawing-ShadowLayer.md) | 返回创建的阴影层对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types;3.Parameter verification failed. |

**示例：**

```ts
import { RenderNode, DrawContext } from '@kit.ArkUI';
import { common2D, drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context : DrawContext) {
    let color : common2D.Color = {alpha: 0xFF, red: 0x00, green: 0xFF, blue: 0x00};
    let shadowLayer = drawing.ShadowLayer.create(3, -3, 3, color);
  }
}
```

## create<sup>18+</sup>

static create(blurRadius: number, x: number, y: number, color: common2D.Color \| number): ShadowLayer

创建阴影层对象。

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名     | 类型      | 必填 | 说明                                 |
| ---------- | -------- | ---- | ----------------------------------- |
| blurRadius  | number   | 是   | 阴影的半径，必须为大于0的浮点数。单位为物理像素px。     |
| x           | number   | 是   | x轴上的偏移量，该参数为浮点数。单位为物理像素px。        |
| y           | number   | 是   | y轴上的偏移量，该参数为浮点数。单位为物理像素px。        |
| color       | [common2D.Color](js-apis-graphics-common2D.md#color) \| number   | 是   | 颜色。为common2D.Color类型时，每个颜色通道的值是[0, 255]的整数；为number类型时，必须是16进制ARGB格式的无符号整数，取值范围为[0, 0xFFFFFFFF]。  |

**返回值：**

| 类型                        | 说明                  |
| --------------------------- | -------------------- |
| [ShadowLayer](arkts-apis-graphics-drawing-ShadowLayer.md) | 返回创建的阴影层对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types;3.Parameter verification failed. |

**示例：**

```ts
import { RenderNode, DrawContext } from '@kit.ArkUI';
import { drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context : DrawContext) {
    let shadowLayer = drawing.ShadowLayer.create(3, -3, 3, 0xff00ff00);
  }
}
```