# Class (RoundRect)

<!--Kit: ArkGraphics 2D-->
<!--Subsystem: Graphics-->
<!--Owner: @hangmengxin-->
<!--Designer: @wangyanglan-->
<!--Tester: @nobuggers-->
<!--Adviser: @ge-yafang-->

圆角矩形对象。

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

## 导入模块

```ts
import { drawing } from '@kit.ArkGraphics2D';
```

## constructor<sup>20+</sup>

constructor(roundRect: RoundRect)

拷贝一个圆角矩形。

**ArkTS模式：** 该接口仅适用于ArkTS-Dyn。

**系统能力：** SystemCapability.Graphics.Drawing

**ArkTS-Dyn起始版本：** 20

**参数：**

| 参数名         | 类型                                       | 必填   | 说明                  |
| ----------- | ---------------------------------------- | ---- | ------------------- |
| roundRect        | [RoundRect](arkts-apis-graphics-drawing-RoundRect.md) | 是    |  用于拷贝的圆角矩形。   |

**示例：**

```ts
import { common2D, drawing } from '@kit.ArkGraphics2D';

let rect: common2D.Rect = {left : 100, top : 100, right : 500, bottom : 300};
let roundRect = new drawing.RoundRect(rect, 50, 50);
let roundRect2 = new drawing.RoundRect(roundRect);
```

## constructor<sup>12+</sup>

ArkTS-Dyn: constructor(rect: common2D.Rect, xRadii: number, yRadii: number)

ArkTS-Sta: constructor(rect: common2D.Rect, xRadii: double, yRadii: double)

构造一个圆角矩形对象，当且仅当xRadii和yRadii均大于0时，圆角生效，否则只会构造一个矩形。

**系统能力：** SystemCapability.Graphics.Drawing

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名         | 类型                                       | 必填   | 说明                  |
| ----------- | ---------------------------------------- | ---- | ------------------- |
| rect        | [common2D.Rect](js-apis-graphics-common2D.md#rect) | 是    | 需要创建的圆角矩形区域。      |
| xRadii        | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 是    | X轴上的圆角半径，该参数为浮点数，小于等于0时无效。     |
| yRadii        | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 是    | Y轴上的圆角半径，该参数为浮点数，小于等于0时无效。     |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**示例：**

```ts
import { common2D, drawing } from '@kit.ArkGraphics2D';

let rect: common2D.Rect = { left: 100.0, top: 100.0, right: 500.0, bottom: 300.0 };
let roundRect = new drawing.RoundRect(rect, 50.0, 50.0);
```

## setCorner<sup>12+</sup>

ArkTS-Dyn: setCorner(pos: CornerPos, x: number, y: number): void

ArkTS-Sta: setCorner(pos: CornerPos, x: double, y: double): void

设置圆角矩形中指定圆角位置的圆角半径。

**系统能力：** SystemCapability.Graphics.Drawing

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名   | 类型                                         | 必填 | 说明                            |
| -------- | -------------------------------------------- | ---- | ------------------------------- |
| pos | [CornerPos](arkts-apis-graphics-drawing-e.md#cornerpos12) | 是   | 圆角位置。                 |
| x     | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 是   | x轴方向的圆角半径，该参数为浮点数，小于等于0时无效。 |
| y     | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 是   | y轴方向的圆角半径，该参数为浮点数，小于等于0时无效。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types;3.Parameter verification failed. |

**示例：**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let roundRect: drawing.RoundRect = new drawing.RoundRect({ left: 0.0, top: 0.0, right: 300.0, bottom: 300.0 }, 50.0, 50.0);
roundRect.setCorner(drawing.CornerPos.TOP_LEFT_POS, 150.0, 150.0);
```

## getCorner<sup>12+</sup>

ArkTS-Dyn: getCorner(pos: CornerPos): common2D.Point

ArkTS-Sta: getCorner(pos: CornerPos): common2D.Point | undefined

获取圆角矩形中指定圆角位置的圆角半径。

**系统能力：** SystemCapability.Graphics.Drawing

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名   | 类型                                         | 必填 | 说明                            |
| -------- | -------------------------------------------- | ---- | ------------------------------- |
| pos | [CornerPos](arkts-apis-graphics-drawing-e.md#cornerpos12) | 是   | 圆角位置。                 |

**返回值：**

| 类型                  | 说明           |
| --------------------- | -------------- |
| ArkTS-Dyn: [common2D.Point](js-apis-graphics-common2D.md#point12)<br/>ArkTS-Sta: [common2D.Point](js-apis-graphics-common2D.md#point12) \| undefined | 返回一个点，其横坐标表示圆角x轴方向上的半径，纵坐标表示y轴方向上的半径。获取失败时返回undefined。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types;3.Parameter verification failed. |

**示例：**

ArkTS-Dyn示例：
```ts
import { drawing } from '@kit.ArkGraphics2D';

let roundRect : drawing.RoundRect = new drawing.RoundRect({left: 0, top: 0, right: 300, bottom: 300}, 50, 50);
let cornerRadius = roundRect.getCorner(drawing.CornerPos.BOTTOM_LEFT_POS);
console.info("getCorner---"+cornerRadius.x)
console.info("getCorner---"+cornerRadius.y)
```

ArkTS-Sta示例：
```ts
import { drawing } from '@kit.ArkGraphics2D';

let roundRect : drawing.RoundRect = new drawing.RoundRect({left: 0.0, top: 0.0, right: 300.0, bottom: 300.0}, 50.0, 50.0);
let cornerRadius = roundRect.getCorner(drawing.CornerPos.BOTTOM_LEFT_POS);
if (cornerRadius != undefined) {
  console.info("getCorner---"+cornerRadius!.x);
  console.info("getCorner---"+cornerRadius!.y);
}
```

## offset<sup>12+</sup>

ArkTS-Dyn: offset(dx: number, dy: number): void

ArkTS-Sta: offset(dx: double, dy: double): void

将圆角矩形分别沿x轴方向和y轴方向平移dx,dy。

**系统能力：** SystemCapability.Graphics.Drawing

**ArkTS-Dyn起始版本：** 12

**ArkTS-Sta起始版本：** 22

**参数：**

| 参数名   | 类型                                         | 必填 | 说明                            |
| -------- | -------------------------------------------- | ---- | ------------------------------- |
| dx | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 是   | 表示x轴方向上的偏移量。正数表示向x轴正方向平移，负数表示向x轴负方向平移，该参数为浮点数。                 |
| dy | ArkTS-Dyn: number<br/>ArkTS-Sta: double | 是   | 表示y轴方向上的偏移量。正数表示向y轴正方向平移，负数表示向y轴负方向平移，该参数为浮点数。                 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)。

| 错误码ID | 错误信息 |
| ------- | --------------------------------------------|
| 401 | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;2.Incorrect parameter types. |

**示例：**

```ts
import { drawing } from '@kit.ArkGraphics2D';

let roundRect : drawing.RoundRect = new drawing.RoundRect({ left: 0, top: 0, right: 300, bottom: 300 }, 50, 50);
roundRect.offset(100, 100);
```