# RoundRect

圆角矩形对象。支持设置和获取指定圆角位置的圆角半径，以及对圆角矩形进行平移操作。

> **说明：**
> 
> - 本Class首批接口从API version 12开始支持。
> 
> - 本模块使用屏幕物理像素单位px。
> 
> - 本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。

**起始版本：** 12

**系统能力：** SystemCapability.Graphics.Drawing

## 导入模块

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';
```

## constructor

```TypeScript
constructor(roundRect: RoundRect)
```

拷贝一个圆角矩形。

**起始版本：** 20

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| roundRect | RoundRect | 是 | 用于拷贝的圆角矩形。 |

**示例**

```TypeScript
import { common2D, drawing } from '@kit.ArkGraphics2D';

let rect: common2D.Rect = {left: 100, top: 100, right: 500, bottom: 300};
let roundRect = new drawing.RoundRect(rect, 50, 50);
let roundRect2 = new drawing.RoundRect(roundRect);
```

## constructor

```TypeScript
constructor(rect: common2D.Rect, xRadii: number, yRadii: number)
```

构造一个圆角矩形对象，当且仅当xRadii和yRadii均大于0时，圆角生效，否则只会构造一个矩形。

**起始版本：** 12

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rect | common2D.Rect | 是 | 需要创建的圆角矩形区域。 |
| xRadii | number | 是 | x轴方向的圆角半径，该参数为浮点数，取值大于0时圆角生效，小于等于0时圆角不生效。 单位为物理像素px。 |
| yRadii | number | 是 | y轴方向的圆角半径，该参数为浮点数，取值大于0时圆角生效，小于等于0时圆角不生效。 单位为物理像素px。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types. |

**示例**

```TypeScript
import { common2D, drawing } from '@kit.ArkGraphics2D';

let rect: common2D.Rect = {left: 100, top: 100, right: 500, bottom: 300};
let roundRect = new drawing.RoundRect(rect, 50, 50);
```

## getCorner

```TypeScript
getCorner(pos: CornerPos): common2D.Point
```

获取圆角矩形中指定圆角位置的圆角半径。

**起始版本：** 12

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pos | [CornerPos](arkts-arkgraphics2d-drawing-cornerpos-e.md) | 是 | 圆角位置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| common2D.Point | 返回一个点，其横坐标表示圆角x轴方向上的半径，纵坐标表示y轴方向上的半径。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

let roundRect: drawing.RoundRect = new drawing.RoundRect({left: 0, top: 0, right: 300, bottom: 300}, 50, 50);
let cornerRadius = roundRect.getCorner(drawing.CornerPos.BOTTOM_LEFT_POS);
console.info("getCorner---" + cornerRadius.x);
console.info("getCorner---" + cornerRadius.y);
```

## offset

```TypeScript
offset(dx: number, dy: number): void
```

将圆角矩形沿x轴方向平移dx、沿y轴方向平移dy。

**起始版本：** 12

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dx | number | 是 | 表示x轴方向上的偏移量。正数表示向x轴正方向平移，负数表示向x轴负方向平移，该参数为浮点数。单位为物理像素px。 |
| dy | number | 是 | 表示y轴方向上的偏移量。正数表示向y轴正方向平移，负数表示向y轴负方向平移，该参数为浮点数。单位为物理像素px。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types. |

**示例**

```TypeScript
import { RenderNode } from '@kit.ArkUI';
import { drawing } from '@kit.ArkGraphics2D';

class DrawingRenderNode extends RenderNode {
  draw(context: DrawContext) {
    const canvas = context.canvas;
    const pen = new drawing.Pen();
    pen.setColor({
      alpha: 255,
      red: 255,
      green: 0,
      blue: 0
    });
    pen.setStrokeWidth(10);
    canvas.attachPen(pen);
    let region = new drawing.Region();
    region.setRect(100, 100, 400, 400);
    region.offset(10, 20);
    canvas.drawPoint(200, 200);
    canvas.drawRegion(region);
    canvas.detachPen();
  }
}
```

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

let roundRect: drawing.RoundRect = new drawing.RoundRect({left: 0, top: 0, right: 300, bottom: 300}, 50, 50);
roundRect.offset(100, 100);
```

## setCorner

```TypeScript
setCorner(pos: CornerPos, x: number, y: number): void
```

设置圆角矩形中指定圆角位置的圆角半径。

**起始版本：** 12

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pos | [CornerPos](arkts-arkgraphics2d-drawing-cornerpos-e.md) | 是 | 圆角位置。 |
| x | number | 是 | x轴方向的圆角半径，该参数为浮点数，取值大于0时该圆角半径设置生效，小于等于0时该圆角半径设置不生效。 单位为物理像素px。 |
| y | number | 是 | y轴方向的圆角半径，该参数为浮点数，取值大于0时该圆角半径设置生效，小于等于0时该圆角半径设置不生效。 单位为物理像素px。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;  2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';

let roundRect: drawing.RoundRect = new drawing.RoundRect({left: 0, top: 0, right: 300, bottom: 300}, 50, 50);
roundRect.setCorner(drawing.CornerPos.TOP_LEFT_POS, 150, 150);
```
