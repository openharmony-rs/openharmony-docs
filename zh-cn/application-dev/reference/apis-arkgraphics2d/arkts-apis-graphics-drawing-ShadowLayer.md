# Class (ShadowLayer)

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @hangmengxin-->
<!--Designer: @wangyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->

> **说明：**
>
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> - 本模块首批接口从API version 11开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> - 本Class首批接口从API version 12开始支持。
>
> - 本模块使用屏幕物理像素单位px。
>
> - 本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。

阴影层对象。

## 导入模块

```ts
import { drawing } from '@kit.ArkGraphics2D';
```

## create<sup>12+</sup>

ArkTS-Dyn: static create(blurRadius: number, x: number, y: number, color: common2D.Color): ShadowLayer

ArkTS-Sta: static create(blurRadius: double, x: double, y: double, color: common2D.Color): ShadowLayer | undefined

创建阴影层对象。

**系统能力：** SystemCapability.Graphics.Drawing

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名     | 类型      | 必填 | 说明                                 |
| ---------- | -------- | ---- | ----------------------------------- |
| blurRadius  | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 是   | 阴影的半径，必须为大于零的浮点数。     |
| x           | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 是   | x轴上的偏移点，该参数为浮点数。        |
| y           | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 是   | Y轴上的偏移点，该参数为浮点数。        |
| color       | [common2D.Color](js-apis-graphics-common2D.md#color) | 是   | ARGB格式的颜色，每个颜色通道的值是0到255之间的整数。 |

**返回值：**

| 类型                        | 说明                  |
| --------------------------- | -------------------- |
| ArkTS-Dyn: [ShadowLayer](arkts-apis-graphics-drawing-ShadowLayer.md)<br/>ArkTS-Sta: [ShadowLayer](arkts-apis-graphics-drawing-ShadowLayer.md) \| undefined | 返回创建的阴影层对象。创建失败时返回undefined。 |

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
    let color : common2D.Color = {alpha: 0xFF, red: 0x00, green: 0xFF, blue: 0x00};
    let shadowLayer = drawing.ShadowLayer.create(3, -3, 3, color);
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
    let color : common2D.Color = {alpha: 0xFF, red: 0x00, green: 0xFF, blue: 0x00};
    let shadowLayer = drawing.ShadowLayer.create(3, -3, 3, color);
  }
}
```

## create<sup>18+</sup>

ArkTS-Dyn: static create(blurRadius: number, x: number, y: number, color: common2D.Color | number): ShadowLayer

ArkTS-Sta: static create(blurRadius: double, x: double, y: double, color: common2D.Color | int): ShadowLayer | undefined

创建阴影层对象。

**系统能力：** SystemCapability.Graphics.Drawing

**ArkTS-Dyn起始版本：** 18

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名     | 类型      | 必填 | 说明                                 |
| ---------- | -------- | ---- | ----------------------------------- |
| blurRadius  | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 是   | 阴影的半径，必须为大于零的浮点数。     |
| x           | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 是   | x轴上的偏移点，该参数为浮点数。        |
| y           | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 是   | Y轴上的偏移点，该参数为浮点数。        |
| color       | ArkTS-Dyn: [common2D.Color](js-apis-graphics-common2D.md#color) \| number<br/>ArkTS-Sta: [common2D.Color](js-apis-graphics-common2D.md#color) \| int    | 是   | 颜色，可以用16进制ARGB格式的无符号整数表示。  |

**返回值：**

| 类型                        | 说明                  |
| --------------------------- | -------------------- |
| ArkTS-Dyn: [ShadowLayer](arkts-apis-graphics-drawing-ShadowLayer.md)<br/>ArkTS-Sta: [ShadowLayer](arkts-apis-graphics-drawing-ShadowLayer.md) \| undefined | 返回创建的阴影层对象。创建失败时返回undefined。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types;3.Parameter verification failed. |

**示例：**

ArkTS-Dyn示例：
```ts
import { RenderNode } from '@kit.ArkUI';
import { drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context : DrawContext) {
    const canvas = context.canvas;
    let shadowLayer = drawing.ShadowLayer.create(3, -3, 3, 0xff00ff00);
  }
}
```

ArkTS-Sta示例：
```ts
import { RenderNode, DrawContext } from '@kit.ArkUI';
import { drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context: DrawContext) {
    const canvas = context.canvas;
    let shadowLayer = drawing.ShadowLayer.create(3.0, -3.0, 3.0, 0xff00ff00);
  }
}
```