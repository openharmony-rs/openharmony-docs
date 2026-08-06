# Canvas

承载绘制内容与绘制状态的载体。 > **说明：** > > - 本模块使用屏幕物理像素单位px。 > > - 本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。 > > **说明：** > > 画布自带一个默认画刷，该画刷为黑色，开启反走样，不具备其他任何样式效果。当画布中没有主动设置画刷和画笔时，该默认画刷生效。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-drawing-class Canvas--><!--Device-drawing-class Canvas-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## attachBrush

```TypeScript
attachBrush(brush: Brush): void
```

绑定画刷到画布上，在画布上进行绘制时，将使用画刷的样式对绘制图形形状的内部进行填充。 > **说明：** > > 执行该方法后，若brush的效果发生改变并且开发者希望该变化生效于接下来的绘制动作，需要再次执行该方法以确保变化生效。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-Canvas-attachBrush(brush: Brush): void--><!--Device-Canvas-attachBrush(brush: Brush): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| brush | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 画刷对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. |

## attachPen

```TypeScript
attachPen(pen: Pen): void
```

绑定画笔到画布上，在画布上进行绘制时，将使用画笔的样式去绘制图形形状的轮廓。 > **说明：** > > 执行该方法后，若pen的效果发生改变并且开发者希望该变化生效于接下来的绘制动作，需要再次执行该方法以确保变化生效。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-Canvas-attachPen(pen: Pen): void--><!--Device-Canvas-attachPen(pen: Pen): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pen | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 画笔对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. |

## clear

```TypeScript
clear(color: common2D.Color): void
```

使用指定颜色填充画布上的裁剪区域。效果等同于[drawColor]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-Canvas-clear(color: common2D.Color): void--><!--Device-Canvas-clear(color: common2D.Color): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | common2D.Color | 是 | ARGB格式的颜色，每个颜色通道的值是0到255之间的整数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. |

## clear

ArkTS-Dyn:
```TypeScript
clear(color: common2D.Color | number): void
```

ArkTS-Sta:
```TypeScript
clear(color: common2D.Color | int): void
```

使用指定颜色填充画布上的裁剪区域。

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-Canvas-clear(color: common2D.Color | int): void--><!--Device-Canvas-clear(color: common2D.Color | int): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | ArkTS-Dyn: common2D.Color \| number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：common2D.Color \| int | 是 | 颜色，可以用16进制ARGB格式的无符号整数表示。 |

## clipPath

```TypeScript
clipPath(path: Path, clipOp?: ClipOp, doAntiAlias?: boolean): void
```

使用自定义路径对画布的可绘制区域进行裁剪。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-Canvas-clipPath(path: Path, clipOp?: ClipOp, doAntiAlias?: boolean): void--><!--Device-Canvas-clipPath(path: Path, clipOp?: ClipOp, doAntiAlias?: boolean): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 路径对象。 |
| clipOp | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 裁剪方式。默认为INTERSECT。 |
| doAntiAlias | boolean | 否 | 表示是否使能抗锯齿绘制。true表示使能，false表示不使能。默认为false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. |

## clipRect

```TypeScript
clipRect(rect: common2D.Rect, clipOp?: ClipOp, doAntiAlias?: boolean): void
```

使用矩形对画布的可绘制区域进行裁剪。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-Canvas-clipRect(rect: common2D.Rect, clipOp?: ClipOp, doAntiAlias?: boolean): void--><!--Device-Canvas-clipRect(rect: common2D.Rect, clipOp?: ClipOp, doAntiAlias?: boolean): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rect | common2D.Rect | 是 | 需要裁剪的矩形区域。 |
| clipOp | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 裁剪方式。默认为INTERSECT。 |
| doAntiAlias | boolean | 否 | 表示是否使能抗锯齿绘制。true表示使能，false表示不使能。默认为false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. |

## clipRegion

```TypeScript
clipRegion(region: Region, clipOp?: ClipOp): void
```

在画布上裁剪一个区域。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-Canvas-clipRegion(region: Region, clipOp?: ClipOp): void--><!--Device-Canvas-clipRegion(region: Region, clipOp?: ClipOp): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| region | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 区域对象，表示裁剪范围。 |
| clipOp | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 裁剪方式，默认为INTERSECT。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. |

## clipRoundRect

```TypeScript
clipRoundRect(roundRect: RoundRect, clipOp?: ClipOp, doAntiAlias?: boolean): void
```

在画布上裁剪一个圆角矩形。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-Canvas-clipRoundRect(roundRect: RoundRect, clipOp?: ClipOp, doAntiAlias?: boolean): void--><!--Device-Canvas-clipRoundRect(roundRect: RoundRect, clipOp?: ClipOp, doAntiAlias?: boolean): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| roundRect | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 圆角矩形对象，表示裁剪范围。 |
| clipOp | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 裁剪方式，默认为INTERSECT。 |
| doAntiAlias | boolean | 否 | 表示是否使能抗锯齿。true表示使能，false表示不使能。默认为false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. |

## concatMatrix

```TypeScript
concatMatrix(matrix: Matrix): void
```

画布现有矩阵左乘传入矩阵，不影响之前的绘制操作，后续绘制操作和裁剪操作的形状和位置都会受到该矩阵的影响。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-Canvas-concatMatrix(matrix: Matrix): void--><!--Device-Canvas-concatMatrix(matrix: Matrix): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| matrix | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 矩阵对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. |

## constructor

```TypeScript
constructor(pixelmap: image.PixelMap)
```

创建一个以PixelMap作为绘制目标的Canvas对象。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-Canvas-constructor(pixelmap: image.PixelMap)--><!--Device-Canvas-constructor(pixelmap: image.PixelMap)-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pixelmap | image.PixelMap | 是 | 构造函数入参。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. |

## detachBrush

```TypeScript
detachBrush(): void
```

将画刷与画布解绑，在画布上进行绘制时，不会再使用画刷对绘制图形形状的内部进行填充。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-Canvas-detachBrush(): void--><!--Device-Canvas-detachBrush(): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## detachPen

```TypeScript
detachPen(): void
```

将画笔与画布解绑，在画布上进行绘制时，不会再使用画笔去绘制图形形状的轮廓。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-Canvas-detachPen(): void--><!--Device-Canvas-detachPen(): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## drawArc

ArkTS-Dyn:
```TypeScript
drawArc(arc: common2D.Rect, startAngle: number, sweepAngle: number): void
```

ArkTS-Sta:
```TypeScript
drawArc(arc: common2D.Rect, startAngle: double, sweepAngle: double): void
```

在画布上绘制圆弧。该方法允许指定起始角度、扫描角度。当扫描角度的绝对值大于360度时，则绘制椭圆。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-Canvas-drawArc(arc: common2D.Rect, startAngle: double, sweepAngle: double): void--><!--Device-Canvas-drawArc(arc: common2D.Rect, startAngle: double, sweepAngle: double): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| arc | common2D.Rect | 是 | 包含要绘制的圆弧的椭圆的矩形边界。 |
| startAngle | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 弧的起始角度，单位为度，该参数为浮点数。0度时起始点位于椭圆的右端点，正数时以顺时针方向放置起始点，负数时以逆时针方向放置起始点。 |
| sweepAngle | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 弧的扫描角度，单位为度，该参数为浮点数。为正数时顺时针扫描，为负数时逆时针扫描。它的有效范围在-360度到360度之间，当绝对值大于360度时，该方法绘制的是一个椭圆。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. |

## drawArcWithCenter

ArkTS-Dyn:
```TypeScript
drawArcWithCenter(arc: common2D.Rect, startAngle: number, sweepAngle: number, useCenter: boolean): void
```

ArkTS-Sta:
```TypeScript
drawArcWithCenter(arc: common2D.Rect, startAngle: double, sweepAngle: double, useCenter: boolean): void
```

在画布上绘制圆弧。该方法允许指定圆弧的起始角度、扫描角度以及圆弧的起点和终点是否连接圆弧的中心点。

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-Canvas-drawArcWithCenter(arc: common2D.Rect, startAngle: double, sweepAngle: double, useCenter: boolean): void--><!--Device-Canvas-drawArcWithCenter(arc: common2D.Rect, startAngle: double, sweepAngle: double, useCenter: boolean): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| arc | common2D.Rect | 是 | 包含要绘制的圆弧的椭圆的矩形边界。 |
| startAngle | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 弧的起始角度，单位为度，该参数为浮点数。0度时起始点位于椭圆的右端点，为正数时以顺时针方向放置起始点，为负数时以逆时针方向放置起始点。 |
| sweepAngle | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 弧的扫描角度，单位为度，该参数为浮点数。为正数时顺时针扫描，为负数时逆时针扫描。扫描角度可以超过360度，将绘制一个完整的椭圆。 |
| useCenter | boolean | 是 | 绘制时弧形的起点和终点是否连接弧形的中心点。true表示连接，false表示不连接。 |

## drawBackground

```TypeScript
drawBackground(brush: Brush): void
```

使用画刷填充画布的可绘制区域。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-Canvas-drawBackground(brush: Brush): void--><!--Device-Canvas-drawBackground(brush: Brush): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| brush | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 画刷对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. |

## drawCircle

ArkTS-Dyn:
```TypeScript
drawCircle(x: number, y: number, radius: number): void
```

ArkTS-Sta:
```TypeScript
drawCircle(x: double, y: double, radius: double): void
```

绘制一个圆形。如果半径小于等于零，则不绘制。默认使用黑色填充。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-Canvas-drawCircle(x: double, y: double, radius: double): void--><!--Device-Canvas-drawCircle(x: double, y: double, radius: double): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 圆心的x坐标，该参数为浮点数。 |
| y | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 圆心的y坐标，该参数为浮点数。 |
| radius | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 圆的半径，大于0的浮点数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types; 3. Parameter verification failed. |

## drawColor

```TypeScript
drawColor(color: common2D.Color, blendMode?: BlendMode): void
```

使用指定颜色并按照指定的[BlendMode]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_对画布当前可绘制区域进行填充。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-Canvas-drawColor(color: common2D.Color, blendMode?: BlendMode): void--><!--Device-Canvas-drawColor(color: common2D.Color, blendMode?: BlendMode): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | common2D.Color | 是 | ARGB格式的颜色，每个颜色通道的值是0到255之间的整数。 |
| blendMode | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 颜色混合模式，默认模式为SRC\_\_\_ESCAPED\_UNDERSCORE\_\_\_OVER。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types; 3. Parameter verification failed. |

## drawColor

ArkTS-Dyn:
```TypeScript
drawColor(alpha: number, red: number, green: number, blue: number, blendMode?: BlendMode): void
```

ArkTS-Sta:
```TypeScript
drawColor(alpha: int, red: int, green: int, blue: int, blendMode?: BlendMode): void
```

使用指定颜色并按照指定的[BlendMode]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_对画布当前可绘制区域进行填充。性能优于 [drawColor]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_接口，推荐使用本接口。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-Canvas-drawColor(alpha: int, red: int, green: int, blue: int, blendMode?: BlendMode): void--><!--Device-Canvas-drawColor(alpha: int, red: int, green: int, blue: int, blendMode?: BlendMode): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| alpha | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | ARGB格式颜色的透明度通道值，该参数是0到255之间的整数，传入范围内的浮点数会向下取整。 |
| red | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | ARGB格式颜色的红色通道值，该参数是0到255之间的整数，传入范围内的浮点数会向下取整。 |
| green | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | ARGB格式颜色的绿色通道值，该参数是0到255之间的整数，传入范围内的浮点数会向下取整。 |
| blue | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | ARGB格式颜色的蓝色通道值，该参数是0到255之间的整数，传入范围内的浮点数会向下取整。 |
| blendMode | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 颜色混合模式，默认模式为SRC\_\_\_ESCAPED\_UNDERSCORE\_\_\_OVER。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types; 3. Parameter verification failed. |

## drawColor

ArkTS-Dyn:
```TypeScript
drawColor(color: number, blendMode?: BlendMode): void
```

ArkTS-Sta:
```TypeScript
drawColor(color: int, blendMode?: BlendMode): void
```

使用指定颜色并按照指定的[BlendMode]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_对画布当前可绘制区域进行填充。

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-Canvas-drawColor(color: int, blendMode?: BlendMode): void--><!--Device-Canvas-drawColor(color: int, blendMode?: BlendMode): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| color | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 16进制ARGB格式的颜色。 |
| blendMode | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 颜色混合模式，默认模式为SRC\_\_\_ESCAPED\_UNDERSCORE\_\_\_OVER。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types; 3. Parameter verification failed. |

## drawGlyphs

ArkTS-Dyn:
```TypeScript
drawGlyphs(glyphIds: Array<number>, glyphIdOffset: number, positions: Array<common2D.Point>,
      positionOffset: number, glyphCount: number, font: Font): void
```

ArkTS-Sta:
```TypeScript
drawGlyphs(glyphIds: Array<int>, glyphIdOffset: int, positions: Array<common2D.Point>,
      positionOffset: int, glyphCount: int, font: Font): void
```

绘制具有指定字体的字形数组。如果字形计数小于或等于0，则不绘制任何内容。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Canvas-drawGlyphs(glyphIds: Array<int>, glyphIdOffset: int, positions: Array<common2D.Point>,      positionOffset: int, glyphCount: int, font: Font): void--><!--Device-Canvas-drawGlyphs(glyphIds: Array<int>, glyphIdOffset: int, positions: Array<common2D.Point>,      positionOffset: int, glyphCount: int, font: Font): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| glyphIds | ArkTS-Dyn: Array&lt;number&gt;  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：Array&lt;int&gt; | 是 | 指示字形ID的数组。 |
| glyphIdOffset | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 指示在绘制字形Ids数组之前要跳过的元素的数量。取值限定为整数。 |
| positions | Array&lt;common2D.Point&gt; | 是 | 表示位置数组。 |
| positionOffset | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 指示在绘制位置数组之前要跳过的元素的数量。取值限定为整数。 |
| glyphCount | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 指示要绘制的字形的数目。取值限定为整数。 |
| font | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 指示用于绘图的字体。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [25900001](../errorcode-drawing.md#25900001-参数值异常) | Parameter error. Possible causes: Incorrect parameter range. |

## drawImage

ArkTS-Dyn:
```TypeScript
drawImage(pixelmap: image.PixelMap, left: number, top: number, samplingOptions?: SamplingOptions): void
```

ArkTS-Sta:
```TypeScript
drawImage(pixelmap: image.PixelMap, left: double, top: double, samplingOptions?: SamplingOptions): void
```

画一张图片，图片的左上角坐标为(left, top)。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-Canvas-drawImage(pixelmap: image.PixelMap, left: double, top: double, samplingOptions?: SamplingOptions): void--><!--Device-Canvas-drawImage(pixelmap: image.PixelMap, left: double, top: double, samplingOptions?: SamplingOptions): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pixelmap | image.PixelMap | 是 | 图片的PixelMap。 |
| left | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 图片位置的左上角x轴坐标，该参数为浮点数。 |
| top | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 图片位置的左上角y轴坐标，该参数为浮点数。 |
| samplingOptions | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 采样选项对象，默认为不使用任何参数构造的原始采样选项对象。\_\_\_HTML\_TAG\_USD\_0\_\_\_**起始版本：** 12 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. |

## drawImageLattice

```TypeScript
drawImageLattice(pixelmap: image.PixelMap, lattice: Lattice, dstRect: common2D.Rect,
      filterMode: FilterMode): void
```

将图像按照矩形网格对象的设置划分为多个网格，并把图像的每个部分按照网格对象的设置绘制到画布上的目标矩形区域。使用此接口时，设置开启抗锯齿无效。 偶数行和列（起始计数为0）的每个交叉点都是固定的，若固定网格区域的尺寸不超过目标矩形，则会在不缩放的情况下被绘制在目标矩形，反之则会按比例缩放绘制在目标矩形；如果还有剩余空间，剩下的区域会通过拉伸或压缩来绘制，以便能够完全覆盖 目标矩形。

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-Canvas-drawImageLattice(pixelmap: image.PixelMap, lattice: Lattice, dstRect: common2D.Rect,      filterMode: FilterMode): void--><!--Device-Canvas-drawImageLattice(pixelmap: image.PixelMap, lattice: Lattice, dstRect: common2D.Rect,      filterMode: FilterMode): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pixelmap | image.PixelMap | 是 | 用于绘制网格的像素图。 |
| lattice | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 矩形网格对象。 |
| dstRect | common2D.Rect | 是 | 目标矩形区域。 |
| filterMode | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 过滤模式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types; 3. Parameter verification failed. |

## drawImageNine

```TypeScript
drawImageNine(pixelmap: image.PixelMap, center: common2D.Rect, dstRect: common2D.Rect,
      filterMode: FilterMode): void
```

通过绘制两条水平线和两条垂直线将图像分割成9个部分：四个边，四个角和中心。使用此接口时，设置开启抗锯齿无效。 若角落的4个区域尺寸不超过目标矩形，则会在不缩放的情况下被绘制在目标矩形，反之则会按比例缩放绘制在目标矩形；如果还有剩余空间，剩下的5个区域会通过拉伸或压缩来绘制，以便能够完全覆盖目标矩形。

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-Canvas-drawImageNine(pixelmap: image.PixelMap, center: common2D.Rect, dstRect: common2D.Rect,      filterMode: FilterMode): void--><!--Device-Canvas-drawImageNine(pixelmap: image.PixelMap, center: common2D.Rect, dstRect: common2D.Rect,      filterMode: FilterMode): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pixelmap | image.PixelMap | 是 | 用于绘制网格的像素图。 |
| center | common2D.Rect | 是 | 分割图像的中心矩形。矩形四条边所在的直线将图像分成了9个部分。 |
| dstRect | common2D.Rect | 是 | 在画布上绘制的目标矩形区域。 |
| filterMode | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 过滤模式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types; 3. Parameter verification failed. |

## drawImageRect

```TypeScript
drawImageRect(pixelmap: image.PixelMap, dstRect: common2D.Rect, samplingOptions?: SamplingOptions): void
```

将图片绘制到画布的指定区域上。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-Canvas-drawImageRect(pixelmap: image.PixelMap, dstRect: common2D.Rect, samplingOptions?: SamplingOptions): void--><!--Device-Canvas-drawImageRect(pixelmap: image.PixelMap, dstRect: common2D.Rect, samplingOptions?: SamplingOptions): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pixelmap | image.PixelMap | 是 | 图片的PixelMap。 |
| dstRect | common2D.Rect | 是 | 矩形对象，用于指定画布上图片的绘制区域。 |
| samplingOptions | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 采样选项对象，默认为不使用任何参数构造的原始采样选项对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. |

## drawImageRectWithSrc

```TypeScript
drawImageRectWithSrc(pixelmap: image.PixelMap, srcRect: common2D.Rect, dstRect: common2D.Rect,
      samplingOptions?: SamplingOptions, constraint?: SrcRectConstraint): void
```

将图片的指定区域绘制到画布的指定区域。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-Canvas-drawImageRectWithSrc(pixelmap: image.PixelMap, srcRect: common2D.Rect, dstRect: common2D.Rect,      samplingOptions?: SamplingOptions, constraint?: SrcRectConstraint): void--><!--Device-Canvas-drawImageRectWithSrc(pixelmap: image.PixelMap, srcRect: common2D.Rect, dstRect: common2D.Rect,      samplingOptions?: SamplingOptions, constraint?: SrcRectConstraint): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pixelmap | image.PixelMap | 是 | 图片的PixelMap。 |
| srcRect | common2D.Rect | 是 | 矩形对象，用于指定图片的待绘制区域。 |
| dstRect | common2D.Rect | 是 | 矩形对象，用于指定画布上图片的绘制区域。 |
| samplingOptions | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 采样选项对象，默认为不使用任何参数构造的原始采样选项对象。 |
| constraint | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 源矩形区域约束类型，默认为STRICT。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. |

## drawLine

ArkTS-Dyn:
```TypeScript
drawLine(x0: number, y0: number, x1: number, y1: number): void
```

ArkTS-Sta:
```TypeScript
drawLine(x0: double, y0: double, x1: double, y1: double): void
```

画一条直线段，从指定的起点到终点。如果直线段的起点和终点是同一个点，无法绘制。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-Canvas-drawLine(x0: double, y0: double, x1: double, y1: double): void--><!--Device-Canvas-drawLine(x0: double, y0: double, x1: double, y1: double): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x0 | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 线段起点的X坐标，该参数为浮点数。 |
| y0 | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 线段起点的Y坐标，该参数为浮点数。 |
| x1 | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 线段终点的X坐标，该参数为浮点数。 |
| y1 | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 线段终点的Y坐标，该参数为浮点数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. |

## drawNestedRoundRect

```TypeScript
drawNestedRoundRect(outer: RoundRect, inner: RoundRect): void
```

绘制两个嵌套的圆角矩形，外部矩形边界必须包含内部矩形边界，否则无绘制效果。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-Canvas-drawNestedRoundRect(outer: RoundRect, inner: RoundRect): void--><!--Device-Canvas-drawNestedRoundRect(outer: RoundRect, inner: RoundRect): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| outer | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 圆角矩形对象，表示外部圆角矩形边界。 |
| inner | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 圆角矩形对象，表示内部圆角矩形边界。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. |

## drawOval

```TypeScript
drawOval(oval: common2D.Rect): void
```

在画布上绘制一个椭圆，椭圆的形状和位置由椭圆的外切矩形给出。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-Canvas-drawOval(oval: common2D.Rect): void--><!--Device-Canvas-drawOval(oval: common2D.Rect): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| oval | common2D.Rect | 是 | 矩形区域，该矩形的内切椭圆即为待绘制椭圆。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. |

## drawPath

```TypeScript
drawPath(path: Path): void
```

绘制一个自定义路径，该路径包含了一组路径轮廓，每个路径轮廓可以是开放的或封闭的。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-Canvas-drawPath(path: Path): void--><!--Device-Canvas-drawPath(path: Path): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 要绘制的路径对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. |

## drawPixelMapMesh

ArkTS-Dyn:
```TypeScript
drawPixelMapMesh(pixelmap: image.PixelMap, meshWidth: number, meshHeight: number,
      vertices: Array<number>, vertOffset: number, colors: Array<number> | null, colorOffset: number): void
```

ArkTS-Sta:
```TypeScript
drawPixelMapMesh(pixelmap: image.PixelMap, meshWidth: int, meshHeight: int,
      vertices: Array<double>, vertOffset: int, colors: Array<int> | null, colorOffset: int): void
```

在网格上绘制像素图，网格均匀分布在像素图上。（只支持brush，使用pen没有绘制效果。）

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-Canvas-drawPixelMapMesh(pixelmap: image.PixelMap, meshWidth: int, meshHeight: int,      vertices: Array<double>, vertOffset: int, colors: Array<int> | null, colorOffset: int): void--><!--Device-Canvas-drawPixelMapMesh(pixelmap: image.PixelMap, meshWidth: int, meshHeight: int,      vertices: Array<double>, vertOffset: int, colors: Array<int> | null, colorOffset: int): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| pixelmap | image.PixelMap | 是 | 用于绘制网格的像素图。 |
| meshWidth | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 网格中的列数，大于0的整数。 |
| meshHeight | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 网格中的行数，大于0的整数。 |
| vertices | ArkTS-Dyn: Array&lt;number&gt;  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：Array&lt;double&gt; | 是 | 顶点数组，指定网格的绘制位置，浮点数组，大小必须为((meshWidth+1) (meshHeight+1) + vertOffset) 2。 |
| vertOffset | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 绘图前要跳过的vert元素数，大于等于0的整数。 |
| colors | ArkTS-Dyn: Array&lt;number&gt; \| null  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：Array&lt;int&gt; \| null | 是 | 颜色数组，在每个顶点指定一种颜色，整数数组，可为null，大小必须为(meshWidth+1) (meshHeight+1) +colorOffset。\_\_\_HTML\_TAG\_USD\_0\_\_\_**起始版本：** 20 |
| colorOffset | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 绘制前要跳过的颜色元素数，大于等于0的整数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. |

## drawPoint

ArkTS-Dyn:
```TypeScript
drawPoint(x: number, y: number): void
```

ArkTS-Sta:
```TypeScript
drawPoint(x: double, y: double): void
```

绘制一个点。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-Canvas-drawPoint(x: double, y: double): void--><!--Device-Canvas-drawPoint(x: double, y: double): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 点的x轴坐标，该参数为浮点数。 |
| y | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 点的y轴坐标，该参数为浮点数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. |

## drawPoints

```TypeScript
drawPoints(points: Array<common2D.Point>, mode?: PointMode): void
```

在画布上绘制一组点、线段或多边形。通过指定点的数组和绘制模式来决定绘制方式。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-Canvas-drawPoints(points: Array<common2D.Point>, mode?: PointMode): void--><!--Device-Canvas-drawPoints(points: Array<common2D.Point>, mode?: PointMode): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| points | Array&lt;common2D.Point&gt; | 是 | 要绘制的点的数组。长度不能为0。 |
| mode | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 绘制数组中的点的方式，默认为drawing.PointMode.POINTS。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types; 3. Parameter verification failed. |

## drawRect

```TypeScript
drawRect(rect: common2D.Rect): void
```

绘制一个矩形，默认使用黑色填充。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-Canvas-drawRect(rect: common2D.Rect): void--><!--Device-Canvas-drawRect(rect: common2D.Rect): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rect | common2D.Rect | 是 | 绘制的矩形区域。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. |

## drawRect

ArkTS-Dyn:
```TypeScript
drawRect(left: number, top: number, right: number, bottom: number): void
```

ArkTS-Sta:
```TypeScript
drawRect(left: double, top: double, right: double, bottom: double): void
```

绘制一个矩形，默认使用黑色填充。性能优于[drawRect]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_接口，推荐使用本接口。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-Canvas-drawRect(left: double, top: double, right: double, bottom: double): void--><!--Device-Canvas-drawRect(left: double, top: double, right: double, bottom: double): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| left | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 矩形的左上角x轴坐标，该参数为浮点数。 |
| top | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 矩形的左上角y轴坐标，该参数为浮点数。 |
| right | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 矩形的右下角x轴坐标，该参数为浮点数。 |
| bottom | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 矩形的右下角y轴坐标，该参数为浮点数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. |

## drawRegion

```TypeScript
drawRegion(region: Region): void
```

绘制一个区域。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-Canvas-drawRegion(region: Region): void--><!--Device-Canvas-drawRegion(region: Region): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| region | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 绘制的区域。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. |

## drawRoundRect

```TypeScript
drawRoundRect(roundRect: RoundRect): void
```

画一个圆角矩形。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-Canvas-drawRoundRect(roundRect: RoundRect): void--><!--Device-Canvas-drawRoundRect(roundRect: RoundRect): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| roundRect | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 圆角矩形对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. |

## drawShadow

ArkTS-Dyn:
```TypeScript
drawShadow(path: Path, planeParams: common2D.Point3d, devLightPos: common2D.Point3d, lightRadius: number,
      ambientColor: common2D.Color, spotColor: common2D.Color, flag: ShadowFlag) : void
```

ArkTS-Sta:
```TypeScript
drawShadow(path: Path, planeParams: common2D.Point3d, devLightPos: common2D.Point3d, lightRadius: double,
      ambientColor: common2D.Color, spotColor: common2D.Color, flag: ShadowFlag) : void
```

绘制射灯类型阴影，使用路径描述环境光阴影的轮廓。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-Canvas-drawShadow(path: Path, planeParams: common2D.Point3d, devLightPos: common2D.Point3d, lightRadius: double,      ambientColor: common2D.Color, spotColor: common2D.Color, flag: ShadowFlag) : void--><!--Device-Canvas-drawShadow(path: Path, planeParams: common2D.Point3d, devLightPos: common2D.Point3d, lightRadius: double,      ambientColor: common2D.Color, spotColor: common2D.Color, flag: ShadowFlag) : void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 路径对象，可生成阴影。 |
| planeParams | common2D.Point3d | 是 | 表示一个三维向量，用于计算遮挡物相对于画布在z轴上的偏移量，其值取决于x与y坐标。 |
| devLightPos | common2D.Point3d | 是 | 光线相对于画布的位置。 |
| lightRadius | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 圆形灯半径，该参数为浮点数。 |
| ambientColor | common2D.Color | 是 | 环境阴影颜色。 |
| spotColor | common2D.Color | 是 | 点阴影颜色。 |
| flag | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 阴影标志枚举。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types; 3. Parameter verification failed. |

## drawShadow

ArkTS-Dyn:
```TypeScript
drawShadow(path: Path, planeParams: common2D.Point3d, devLightPos: common2D.Point3d, lightRadius: number,
      ambientColor: common2D.Color | number, spotColor: common2D.Color | number, flag: ShadowFlag) : void
```

ArkTS-Sta:
```TypeScript
drawShadow(path: Path, planeParams: common2D.Point3d, devLightPos: common2D.Point3d, lightRadius: double,
      ambientColor: common2D.Color | int, spotColor: common2D.Color | int, flag: ShadowFlag) : void
```

绘制射灯类型阴影，使用路径描述环境光阴影的轮廓。

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-Canvas-drawShadow(path: Path, planeParams: common2D.Point3d, devLightPos: common2D.Point3d, lightRadius: double,      ambientColor: common2D.Color | int, spotColor: common2D.Color | int, flag: ShadowFlag) : void--><!--Device-Canvas-drawShadow(path: Path, planeParams: common2D.Point3d, devLightPos: common2D.Point3d, lightRadius: double,      ambientColor: common2D.Color | int, spotColor: common2D.Color | int, flag: ShadowFlag) : void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 路径对象，可生成阴影。 |
| planeParams | common2D.Point3d | 是 | 表示一个三维向量，用于计算z轴方向的偏移量。 |
| devLightPos | common2D.Point3d | 是 | 光线相对于画布的位置。 |
| lightRadius | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 圆形灯半径，该参数为浮点数。 |
| ambientColor | ArkTS-Dyn: common2D.Color \| number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：common2D.Color \| int | 是 | 环境阴影颜色，可以用16进制ARGB格式的32位无符号整数表示。 |
| spotColor | ArkTS-Dyn: common2D.Color \| number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：common2D.Color \| int | 是 | 点阴影颜色，可以用16进制ARGB格式的32位无符号整数表示。 |
| flag | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 阴影标志枚举。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types; 3. Parameter verification failed. |

## drawSingleCharacter

ArkTS-Dyn:
```TypeScript
drawSingleCharacter(text: string, font: Font, x: number, y: number): void
```

ArkTS-Sta:
```TypeScript
drawSingleCharacter(text: string, font: Font, x: double, y: double): void
```

绘制单个字符。当前字型中的字体不支持待绘制字符时，退化到使用系统字体绘制字符。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-Canvas-drawSingleCharacter(text: string, font: Font, x: double, y: double): void--><!--Device-Canvas-drawSingleCharacter(text: string, font: Font, x: double, y: double): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 待绘制的单个字符，字符串的长度必须为1。 |
| font | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 字型对象。 |
| x | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 所绘制出的字符基线（下图蓝线）的左端点（下图红点）的横坐标，该参数为浮点数。 |
| y | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 所绘制出的字符基线（下图蓝线）的左端点（下图红点）的纵坐标，该参数为浮点数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types; 3. Parameter verification failed. |

## drawSingleCharacterWithFeatures

ArkTS-Dyn:
```TypeScript
drawSingleCharacterWithFeatures(text: string, font: Font, x: number, y: number, features: Array<FontFeature>): void
```

ArkTS-Sta:
```TypeScript
drawSingleCharacterWithFeatures(text: string, font: Font, x: double, y: double, features: Array<FontFeature>): void
```

绘制单个字符，字符带有字体特征。当前字型中的字体不支持待绘制字符时，退化到使用系统字体绘制字符。

**起始版本：** 20

**ArkTS模式：** ArkTS-Dyn起始版本为20；ArkTS-Sta起始版本为24。

<!--Device-Canvas-drawSingleCharacterWithFeatures(text: string, font: Font, x: double, y: double, features: Array<FontFeature>): void--><!--Device-Canvas-drawSingleCharacterWithFeatures(text: string, font: Font, x: double, y: double, features: Array<FontFeature>): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 待绘制的单个字符，字符串长度必须为1。 |
| font | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 字型对象。 |
| x | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 所绘制字符基线左端点的横坐标，该参数为浮点数。 |
| y | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 所绘制字符基线左端点的纵坐标，该参数为浮点数。 |
| features | Array&lt;FontFeature&gt; | 是 | 字体特征对象数组。参数为空数组时使用TTF(TrueType Font)文件中预设的字体特征。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [25900001](../errorcode-drawing.md#25900001-参数值异常) | Parameter error. Possible causes: Incorrect parameter range. |

## drawTextBlob

ArkTS-Dyn:
```TypeScript
drawTextBlob(blob: TextBlob, x: number, y: number): void
```

ArkTS-Sta:
```TypeScript
drawTextBlob(blob: TextBlob, x: double, y: double): void
```

绘制一段文字。若构造blob的字体不支持待绘制字符，则该部分字符无法绘制。

**起始版本：** 11

**ArkTS模式：** ArkTS-Dyn起始版本为11；ArkTS-Sta起始版本为23。

<!--Device-Canvas-drawTextBlob(blob: TextBlob, x: double, y: double): void--><!--Device-Canvas-drawTextBlob(blob: TextBlob, x: double, y: double): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| blob | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | TextBlob对象。 |
| x | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 所绘制出的文字基线（下图蓝线）的左端点（下图红点）的横坐标，该参数为浮点数。 |
| y | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 所绘制出的文字基线（下图蓝线）的左端点（下图红点）的纵坐标，该参数为浮点数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. |

## drawVertices

ArkTS-Dyn:
```TypeScript
drawVertices(vertexMode: VertexMode, vertexCount: number, positions: Array<common2D.Point>,
      texs: Array<common2D.Point> | null, colors: Array<number> | null, indexCount: number,
      indices: Array<number> | null, mode: BlendMode): void
```

ArkTS-Sta:
```TypeScript
drawVertices(vertexMode: VertexMode, vertexCount: int, positions: Array<common2D.Point>,
      texs: Array<common2D.Point> | null, colors: Array<int> | null, indexCount: int,
      indices: Array<int> | null, mode: BlendMode): void
```

绘制顶点数组描述的三角网格。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-Canvas-drawVertices(vertexMode: VertexMode, vertexCount: int, positions: Array<common2D.Point>,      texs: Array<common2D.Point> | null, colors: Array<int> | null, indexCount: int,      indices: Array<int> | null, mode: BlendMode): void--><!--Device-Canvas-drawVertices(vertexMode: VertexMode, vertexCount: int, positions: Array<common2D.Point>,      texs: Array<common2D.Point> | null, colors: Array<int> | null, indexCount: int,      indices: Array<int> | null, mode: BlendMode): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| vertexMode | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 绘制顶点的连接方式。 |
| vertexCount | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 顶点数组元素的数量，值为大于等于3的整数。 |
| positions | Array&lt;common2D.Point&gt; | 是 | 描述顶点位置的数组，不能为空，其长度必须等于vertexCount。 |
| texs | Array&lt;common2D.Point&gt; \| null | 是 | 描述顶点对应纹理空间坐标的数组。其可以为空，表明纹理空间失效；若不为空，其长度必须等于vertexCount。 |
| colors | ArkTS-Dyn: Array&lt;number&gt; \| null  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：Array&lt;int&gt; \| null | 是 | 描述顶点对应颜色的数组，用于在三角形中进行插值。其可以为空，表明颜色效果为用户所设置的默认色；若不为空其长度必须等于vertexCount。 |
| indexCount | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 索引的数量。其值可以为0，且indices数组长度为0时可以画图；若不为0，则值必须为大于等于3的整数。 |
| indices | ArkTS-Dyn: Array&lt;number&gt; \| null  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：Array&lt;int&gt; \| null | 是 | 描述顶点对应索引的数组。其可以为空，此时将忽略indexCount的合理传值（大于等于3的整数或等于0）；若不为空其长度必须等于indexCount。 |
| mode | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 颜色混合模式。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [25900001](../errorcode-drawing.md#25900001-参数值异常) | Parameter error. Possible causes: Incorrect parameter range. |

## getHeight

ArkTS-Dyn:
```TypeScript
getHeight(): number
```

ArkTS-Sta:
```TypeScript
getHeight(): int
```

获取画布的高度。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-Canvas-getHeight(): int--><!--Device-Canvas-getHeight(): int-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 返回画布的高度，该参数为浮点数。 |

## getLocalClipBounds

```TypeScript
getLocalClipBounds(): common2D.Rect
```

获取画布裁剪区域的边界。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

<!--Device-Canvas-getLocalClipBounds(): common2D.Rect--><!--Device-Canvas-getLocalClipBounds(): common2D.Rect-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| common2D.Rect | Bounds of the cropping region. |

## getLocalClipBounds

```TypeScript
getLocalClipBounds(): common2D.Rect | undefined
```

Obtains the bounds of the cropping region of the canvas.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-Canvas-getLocalClipBounds(): common2D.Rect | undefined--><!--Device-Canvas-getLocalClipBounds(): common2D.Rect | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| common2D.Rect | Rect object. |

## getSaveCount

ArkTS-Dyn:
```TypeScript
getSaveCount(): number
```

ArkTS-Sta:
```TypeScript
getSaveCount(): int
```

获取栈中保存的画布状态（画布矩阵和裁剪区域）的数量。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-Canvas-getSaveCount(): int--><!--Device-Canvas-getSaveCount(): int-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 已保存的画布状态的数量，该参数为正整数。 |

## getTotalMatrix

```TypeScript
getTotalMatrix(): Matrix
```

获取画布矩阵。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

<!--Device-Canvas-getTotalMatrix(): Matrix--><!--Device-Canvas-getTotalMatrix(): Matrix-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | 返回画布矩阵。 |

## getTotalMatrix

```TypeScript
getTotalMatrix(): Matrix | undefined
```

Obtains the canvas matrix.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-Canvas-getTotalMatrix(): Matrix | undefined--><!--Device-Canvas-getTotalMatrix(): Matrix | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| \_\_\_MD\_LINK\_USD\_0\_\_\_ | Canvas matrix. |

## getWidth

ArkTS-Dyn:
```TypeScript
getWidth(): number
```

ArkTS-Sta:
```TypeScript
getWidth(): int
```

获取画布的宽度。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-Canvas-getWidth(): int--><!--Device-Canvas-getWidth(): int-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 返回画布的宽度，该参数为浮点数。 |

## isClipEmpty

```TypeScript
isClipEmpty(): boolean
```

判断裁剪后的可绘制区域是否为空。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-Canvas-isClipEmpty(): boolean--><!--Device-Canvas-isClipEmpty(): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回画布的可绘制区域是否为空的结果，true表示为空，false表示不为空。 |

## isOpaque

```TypeScript
isOpaque(): boolean
```

检查绘制到设备中的当前图层是否不透明。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Canvas-isOpaque(): boolean--><!--Device-Canvas-isOpaque(): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果绘制到设备中的当前层是不透明的，则返回true。 |

## quickRejectPath

```TypeScript
quickRejectPath(path: Path): boolean
```

判断路径与画布区域是否不相交。画布区域包含边界。

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-Canvas-quickRejectPath(path: Path): boolean--><!--Device-Canvas-quickRejectPath(path: Path): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 路径对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回路径是否与画布区域不相交的结果。true表示路径与画布区域不相交，false表示路径与画布区域相交。 |

## quickRejectRect

```TypeScript
quickRejectRect(rect: common2D.Rect): boolean
```

判断矩形和画布区域是否不相交。画布区域包含边界。

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-Canvas-quickRejectRect(rect: common2D.Rect): boolean--><!--Device-Canvas-quickRejectRect(rect: common2D.Rect): boolean-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rect | common2D.Rect | 是 | 矩形区域。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 返回矩形是否与画布区域不相交的结果。true表示矩形与画布区域不相交，false表示矩形与画布区域相交。 |

## resetClip

```TypeScript
resetClip(): void
```

将当前画布的裁剪状态重置为初始状态。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Canvas-resetClip(): void--><!--Device-Canvas-resetClip(): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## resetMatrix

```TypeScript
resetMatrix(): void
```

将当前画布的矩阵重置为单位矩阵。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-Canvas-resetMatrix(): void--><!--Device-Canvas-resetMatrix(): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## restore

```TypeScript
restore(): void
```

恢复保存在栈顶的画布状态（画布矩阵和裁剪区域）。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-Canvas-restore(): void--><!--Device-Canvas-restore(): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## restoreToCount

ArkTS-Dyn:
```TypeScript
restoreToCount(count: number): void
```

ArkTS-Sta:
```TypeScript
restoreToCount(count: int): void
```

恢复到指定数量的画布状态（画布矩阵和裁剪区域）。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-Canvas-restoreToCount(count: int): void--><!--Device-Canvas-restoreToCount(count: int): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| count | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 要恢复的画布状态深度，该参数为整数。小于等于1时，恢复为初始状态；大于已保存的画布状态数量时，不执行任何操作。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. |

## rotate

ArkTS-Dyn:
```TypeScript
rotate(degrees: number, sx: number, sy: number) : void
```

ArkTS-Sta:
```TypeScript
rotate(degrees: double, sx: double, sy: double) : void
```

在当前画布矩阵（默认是单位矩阵）的基础上再叠加一个旋转矩阵，后续绘制操作和裁剪操作的形状和位置都会自动叠加一个旋转效果。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-Canvas-rotate(degrees: double, sx: double, sy: double) : void--><!--Device-Canvas-rotate(degrees: double, sx: double, sy: double) : void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| degrees | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 旋转角度，单位为度，该参数为浮点数，正数为顺时针旋转，负数为逆时针旋转。 |
| sx | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 旋转中心的横坐标，该参数为浮点数。 |
| sy | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | 旋转中心的纵坐标，该参数为浮点数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. |

## save

ArkTS-Dyn:
```TypeScript
save(): number
```

ArkTS-Sta:
```TypeScript
save(): int
```

保存当前画布状态（画布矩阵和可绘制区域）到栈顶。需要与恢复接口[restore]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_配合使用。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-Canvas-save(): int--><!--Device-Canvas-save(): int-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 画布状态个数，该参数为正整数。 |

## saveLayer

ArkTS-Dyn:
```TypeScript
saveLayer(rect?: common2D.Rect | null, brush?: Brush | null): number
```

ArkTS-Sta:
```TypeScript
saveLayer(rect?: common2D.Rect | null, brush?: Brush | null): long
```

保存当前画布的矩阵和裁剪区域，并为后续绘制分配位图。调用恢复接口[restore]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_将会舍弃对矩阵和裁剪区域做的更改，并绘制位图。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-Canvas-saveLayer(rect?: common2D.Rect | null, brush?: Brush | null): long--><!--Device-Canvas-saveLayer(rect?: common2D.Rect | null, brush?: Brush | null): long-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rect | common2D.Rect \| null | 否 | 矩形对象，用于限制图层大小，默认为当前画布大小。 |
| brush | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| null | 否 | 画刷对象，绘制位图时会应用画刷对象的透明度，颜色滤波器效果和混合模式，默认不设置额外效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：long | 返回调用前保存的画布状态数，该参数为正整数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: Mandatory parameters are left unspecified. |

## scale

ArkTS-Dyn:
```TypeScript
scale(sx: number, sy: number): void
```

ArkTS-Sta:
```TypeScript
scale(sx: double, sy: double): void
```

在当前画布矩阵（默认是单位矩阵）的基础上再叠加一个缩放矩阵，后续绘制操作和裁剪操作的形状和位置都会自动叠加一个缩放效果。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-Canvas-scale(sx: double, sy: double): void--><!--Device-Canvas-scale(sx: double, sy: double): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sx | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | x轴方向的缩放比例，该参数为浮点数。 |
| sy | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | y轴方向的缩放比例，该参数为浮点数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. |

## setMatrix

```TypeScript
setMatrix(matrix: Matrix): void
```

设置画布的矩阵，后续绘制操作和裁剪操作的形状和位置都会受到该矩阵的影响。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-Canvas-setMatrix(matrix: Matrix): void--><!--Device-Canvas-setMatrix(matrix: Matrix): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| matrix | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 矩阵对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. |

## skew

ArkTS-Dyn:
```TypeScript
skew(sx: number, sy: number) : void
```

ArkTS-Sta:
```TypeScript
skew(sx: double, sy: double) : void
```

在当前画布矩阵（默认是单位矩阵）的基础上再叠加一个倾斜矩阵，后续绘制操作和裁剪操作的形状和位置都会自动叠加一个倾斜效果。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-Canvas-skew(sx: double, sy: double) : void--><!--Device-Canvas-skew(sx: double, sy: double) : void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sx | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | x轴上的倾斜量，该参数为浮点数。正值会使绘制沿y轴增量方向向右倾斜；负值会使绘制沿y轴增量方向向左倾斜。 |
| sy | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | y轴上的倾斜量，该参数为浮点数。正值会使绘制沿x轴增量方向向下倾斜；负值会使绘制沿x轴增量方向向上倾斜。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. |

## translate

ArkTS-Dyn:
```TypeScript
translate(dx: number, dy: number): void
```

ArkTS-Sta:
```TypeScript
translate(dx: double, dy: double): void
```

在当前画布矩阵（默认是单位矩阵）的基础上再叠加一个平移矩阵，后续绘制操作和裁剪操作的形状和位置都会自动叠加一个平移效果。

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-Canvas-translate(dx: double, dy: double): void--><!--Device-Canvas-translate(dx: double, dy: double): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| dx | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | x轴方向的移动距离，该参数为浮点数。 |
| dy | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：double | 是 | y轴方向的移动距离，该参数为浮点数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. |

