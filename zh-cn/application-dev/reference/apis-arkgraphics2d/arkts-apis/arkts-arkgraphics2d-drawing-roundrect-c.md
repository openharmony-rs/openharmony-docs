# RoundRect

圆角矩形对象。
> **说明：**  
>  
> - 本Class首批接口从API version 12开始支持。  
>  
> - 本模块使用屏幕物理像素单位px。  
>  
> - 本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。

**起始版本：** 12

<!--Device-drawing-class RoundRect--><!--Device-drawing-class RoundRect-End-->

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

<!--Device-RoundRect-constructor(roundRect: RoundRect)--><!--Device-RoundRect-constructor(roundRect: RoundRect)-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| roundRect | [RoundRect](arkts-arkgraphics2d-drawing-roundrect-c.md) | 是 | 用于拷贝的圆角矩形。 |

## constructor

```TypeScript
constructor(rect: common2D.Rect, xRadii: number, yRadii: number)
```

构造一个圆角矩形对象，当且仅当xRadii和yRadii均大于0时，圆角生效，否则只会构造一个矩形。

**起始版本：** 12

<!--Device-RoundRect-constructor(rect: common2D.Rect, xRadii: double, yRadii: double)--><!--Device-RoundRect-constructor(rect: common2D.Rect, xRadii: double, yRadii: double)-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rect | common2D.Rect | 是 | 需要创建的圆角矩形区域。 |
| xRadii | number | 是 | X轴上的圆角半径，该参数为浮点数，小于等于0时无效。 |
| yRadii | number | 是 | Y轴上的圆角半径，该参数为浮点数，小于等于0时无效。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## getCorner

```TypeScript
getCorner(pos: CornerPos): common2D.Point
```

获取圆角矩形中指定圆角位置的圆角半径。

**起始版本：** 12

<!--Device-RoundRect-getCorner(pos: CornerPos): common2D.Point--><!--Device-RoundRect-getCorner(pos: CornerPos): common2D.Point-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pos | [CornerPos](arkts-arkgraphics2d-drawing-cornerpos-e.md) | 是 | 圆角位置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| common2D.Point | Point. The horizontal coordinate indicates the radius of the rounded corner on the X axis, and the vertical coordinate indicates the radius on the Y axis. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

## offset

```TypeScript
offset(dx: number, dy: number): void
```

将圆角矩形分别沿x轴方向和y轴方向平移dx,dy。

**起始版本：** 12

<!--Device-RoundRect-offset(dx: double, dy: double): void--><!--Device-RoundRect-offset(dx: double, dy: double): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dx | number | 是 | 表示x轴方向上的偏移量。正数表示向x轴正方向平移，负数表示向x轴负方向平移，该参数为浮点数。 |
| dy | number | 是 | 表示y轴方向上的偏移量。正数表示向y轴正方向平移，负数表示向y轴负方向平移，该参数为浮点数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |

## setCorner

```TypeScript
setCorner(pos: CornerPos, x: number, y: number): void
```

设置圆角矩形中指定圆角位置的圆角半径。

**起始版本：** 12

<!--Device-RoundRect-setCorner(pos: CornerPos, x: double, y: double): void--><!--Device-RoundRect-setCorner(pos: CornerPos, x: double, y: double): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pos | [CornerPos](arkts-arkgraphics2d-drawing-cornerpos-e.md) | 是 | 圆角位置。 |
| x | number | 是 | x轴方向的圆角半径，该参数为浮点数，小于等于0时无效。 |
| y | number | 是 | y轴方向的圆角半径，该参数为浮点数，小于等于0时无效。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

