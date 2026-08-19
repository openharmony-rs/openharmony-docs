# PathEffect

路径效果对象，用于创建多种路径效果，包括虚线、圆角、离散、叠加和组合路径效果等。可通过[Pen.setPathEffect](arkts-arkgraphics2d-drawing-pen-c.md#setpatheffect)将其应用到画笔上，从而在绘制路径时改变路 径的渲染样式。 > **说明：** > > - 本Class首批接口从API version 12开始支持。 > > - 本模块使用屏幕物理像素单位px。 > > - 本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。

**起始版本：** 23

<!--Device-drawing-class PathEffect--><!--Device-drawing-class PathEffect-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## 导入模块

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';
```

## createComposePathEffect

```TypeScript
static createComposePathEffect(outer: PathEffect, inner: PathEffect): PathEffect
```

创建组合路径效果对象，首先应用内部路径效果，然后应用外部路径效果。

**起始版本：** 18

<!--Device-PathEffect-static createComposePathEffect(outer: PathEffect, inner: PathEffect): PathEffect--><!--Device-PathEffect-static createComposePathEffect(outer: PathEffect, inner: PathEffect): PathEffect-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| outer | [PathEffect](arkts-arkgraphics2d-drawing-patheffect-c.md) | 是 | 组合路径效果中的外部路径效果，在内部路径效果应用之后进行叠加处理，决定最终呈现的叠加效果。 |
| inner | [PathEffect](arkts-arkgraphics2d-drawing-patheffect-c.md) | 是 | 组合路径效果中的内部路径效果，首先应用于原始路径，作为第一层效果处理，随后再由外部路径效果进行叠加。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PathEffect](arkts-arkgraphics2d-drawing-patheffect-c.md) | 返回创建的组合路径效果对象，可通过[Pen.setPathEffect]{ |

## createComposePathEffect

```TypeScript
static createComposePathEffect(outer: PathEffect, inner: PathEffect): PathEffect | undefined
```

创建组合路径效果对象，首先应用内部路径效果，然后应用外部路径效果。

**起始版本：** 23

<!--Device-PathEffect-static createComposePathEffect(outer: PathEffect, inner: PathEffect): PathEffect | undefined--><!--Device-PathEffect-static createComposePathEffect(outer: PathEffect, inner: PathEffect): PathEffect | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| outer | [PathEffect](arkts-arkgraphics2d-drawing-patheffect-c.md) | 是 | 组合路径效果中的外部路径效果，在内部路径效果应用之后进行叠加处理，决定最终呈现的叠加效果。 |
| inner | [PathEffect](arkts-arkgraphics2d-drawing-patheffect-c.md) | 是 | 组合路径效果中的内部路径效果，首先应用于原始路径，作为第一层效果处理，随后再由外部路径效果进行叠加。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PathEffect](arkts-arkgraphics2d-drawing-patheffect-c.md) | 返回创建的组合路径效果对象，可通过[Pen.setPathEffect]{ |

## createCornerPathEffect

```TypeScript
static createCornerPathEffect(radius: number): PathEffect
```

创建将路径的夹角变成指定半径的圆角的路径效果对象。该效果会在路径的每个夹角处插入指定半径的弧线段，将原有的尖锐转角替换为平滑的圆角过渡。

**起始版本：** 12

<!--Device-PathEffect-static createCornerPathEffect(radius: number): PathEffect--><!--Device-PathEffect-static createCornerPathEffect(radius: number): PathEffect-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| radius | number | 是 | 圆角的半径，取值范围>0，该参数为浮点数。单位为物理像素px。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PathEffect](arkts-arkgraphics2d-drawing-patheffect-c.md) | 返回创建的圆角路径效果对象，可通过[Pen.setPathEffect]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; 3. Parameter verification failed. |

## createCornerPathEffect

```TypeScript
static createCornerPathEffect(radius: double): PathEffect | undefined
```

创建将路径的夹角变成指定半径的圆角的路径效果对象。该效果会在路径的每个夹角处插入指定半径的弧线段，将原有的尖锐转角替换为平滑的圆角过渡。

**起始版本：** 23

<!--Device-PathEffect-static createCornerPathEffect(radius: double): PathEffect | undefined--><!--Device-PathEffect-static createCornerPathEffect(radius: double): PathEffect | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| radius | double | 是 | 圆角的半径，取值范围>0，该参数为浮点数。单位为物理像素px。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PathEffect](arkts-arkgraphics2d-drawing-patheffect-c.md) | 返回创建的圆角路径效果对象，可通过[Pen.setPathEffect]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; 3. Parameter verification failed. |

## createDashPathEffect

```TypeScript
static createDashPathEffect(intervals: Array<number>, phase: number): PathEffect
```

创建将路径变为虚线的路径效果对象，通过指定ON/OFF长度数组生成规则间距的虚线。当需要自定义形状作为虚线段填充时，可使用 [createPathDashEffect](#createpathdasheffect)。

**起始版本：** 12

<!--Device-PathEffect-static createDashPathEffect(intervals: Array<number>, phase: number): PathEffect--><!--Device-PathEffect-static createDashPathEffect(intervals: Array<number>, phase: number): PathEffect-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| intervals | Array&lt;number&gt; | 是 | 表示虚线的ON（实线部分）和OFF（空白部分）长度的数组，数组元素个数必须是偶数且>=2，数组元素为正整数。单位为物理像素px。 |
| phase | number | 是 | 绘制时的偏移量，用于调整虚线图案沿路径的起始位置，该参数为浮点数，偏移量会相对于intervals定义的虚线模式产生位移效果。单位为物理像素px。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PathEffect](arkts-arkgraphics2d-drawing-patheffect-c.md) | 返回创建的虚线路径效果对象，可通过[Pen.setPathEffect]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; 3. Parameter verification failed. |

## createDashPathEffect

```TypeScript
static createDashPathEffect(intervals: Array<double>, phase: double): PathEffect | undefined
```

创建将路径变为虚线的路径效果对象，通过指定ON/OFF长度数组生成规则间距的虚线。当需要自定义形状作为虚线段填充时，可使用 [createPathDashEffect](#createpathdasheffect)。

**起始版本：** 23

<!--Device-PathEffect-static createDashPathEffect(intervals: Array<double>, phase: double): PathEffect | undefined--><!--Device-PathEffect-static createDashPathEffect(intervals: Array<double>, phase: double): PathEffect | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| intervals | Array&lt;double&gt; | 是 | 表示虚线的ON（实线部分）和OFF（空白部分）长度的数组，数组元素个数必须是偶数且>=2，数组元素为正整数。单位为物理像素px。 |
| phase | double | 是 | 绘制时的偏移量，用于调整虚线图案沿路径的起始位置，该参数为浮点数，偏移量会相对于intervals定义的虚线模式产生位移效果。单位为物理像素px。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PathEffect](arkts-arkgraphics2d-drawing-patheffect-c.md) | 返回创建的虚线路径效果对象，可通过[Pen.setPathEffect]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; 3. Parameter verification failed. |

## createDiscretePathEffect

```TypeScript
static createDiscretePathEffect(segLength: number, dev: number, seedAssist?: number): PathEffect
```

创建将路径打散为离散线段并对端点进行随机偏移的路径效果对象。

**起始版本：** 18

<!--Device-PathEffect-static createDiscretePathEffect(segLength: number, dev: number, seedAssist?: number): PathEffect--><!--Device-PathEffect-static createDiscretePathEffect(segLength: number, dev: number, seedAssist?: number): PathEffect-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| segLength | number | 是 | 路径中每进行一次打散操作的长度，该参数为浮点数，传入负数或0时无效果。单位为物理像素px。 |
| dev | number | 是 | 绘制时每个离散线段端点的最大移动偏离量，该偏离量为浮点数。单位为物理像素px。 |
| seedAssist | number | 否 | 用于生成离散效果的伪随机种子，影响路径打散的随机分布模式。当需要可复现的离散效果时传入指定种子值；当不需要特定随机分布模式时可省略此参数，省略时默认值为0。该参 数为32位无符号整数。超出范围时，该参数值按32位无符号整数溢出回绕规则处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PathEffect](arkts-arkgraphics2d-drawing-patheffect-c.md) | 返回创建的离散路径效果对象，可通过[Pen.setPathEffect]{ |

## createDiscretePathEffect

```TypeScript
static createDiscretePathEffect(segLength: double, dev: double, seedAssist?: int): PathEffect | undefined
```

创建将路径打散为离散线段并对端点进行随机偏移的路径效果对象。

**起始版本：** 23

<!--Device-PathEffect-static createDiscretePathEffect(segLength: double, dev: double, seedAssist?: int): PathEffect | undefined--><!--Device-PathEffect-static createDiscretePathEffect(segLength: double, dev: double, seedAssist?: int): PathEffect | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| segLength | double | 是 | 路径中每进行一次打散操作的长度，该参数为浮点数，传入负数或0时无效果。单位为物理像素px。 |
| dev | double | 是 | 绘制时每个离散线段端点的最大移动偏离量，该偏离量为浮点数。单位为物理像素px。 |
| seedAssist | int | 否 | 用于生成离散效果的伪随机种子，影响路径打散的随机分布模式。当需要可复现的离散效果时传入指定种子值；当不需要特定随机分布模式时可省略此参数，省略时默认值为0。该参 数为32位无符号整数。超出范围时，该参数值按32位无符号整数溢出回绕规则处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PathEffect](arkts-arkgraphics2d-drawing-patheffect-c.md) | 返回创建的离散路径效果对象，可通过[Pen.setPathEffect]{ |

## createPathDashEffect

```TypeScript
static createPathDashEffect(path: Path, advance: number, phase: number, style: PathDashStyle): PathEffect
```

创建一个虚线路径效果对象，通过路径描述的形状生成。与 [createDashPathEffect](#createdashpatheffect)使用 intervals数组指定ON/OFF长度创建规则间距虚线不同，本接口通过Path指定虚线段的图形形状。

**起始版本：** 18

<!--Device-PathEffect-static createPathDashEffect(path: Path, advance: number, phase: number, style: PathDashStyle): PathEffect--><!--Device-PathEffect-static createPathDashEffect(path: Path, advance: number, phase: number, style: PathDashStyle): PathEffect-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | Path | 是 | 通过该路径生成一个图形，用来填充每个虚线段。 |
| advance | number | 是 | 虚线段的步长，取值范围>0，否则会抛错误码。单位为物理像素px。 |
| phase | number | 是 | 表示虚线段内图形在虚线步长范围内的偏移量，该参数为浮点数，效果为先对偏移量取绝对值，然后对步长取模。单位为物理像素px。 |
| style | [PathDashStyle](arkts-arkgraphics2d-drawing-pathdashstyle-e.md) | 是 | 指定虚线效果的样式，决定虚线段图形在路径上的变换方式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PathEffect](arkts-arkgraphics2d-drawing-patheffect-c.md) | 返回创建的虚线路径效果对象，可通过[Pen.setPathEffect]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; 3. Parameter verification failed. |

## createPathDashEffect

```TypeScript
static createPathDashEffect(path: Path, advance: double, phase: double,
        style: PathDashStyle): PathEffect | undefined
```

创建一个虚线路径效果对象，通过路径描述的形状生成。与 [createDashPathEffect](#createdashpatheffect)使用 intervals数组指定ON/OFF长度创建规则间距虚线不同，本接口通过Path指定虚线段的图形形状。

**起始版本：** 23

<!--Device-PathEffect-static createPathDashEffect(path: Path, advance: double, phase: double,        style: PathDashStyle): PathEffect | undefined--><!--Device-PathEffect-static createPathDashEffect(path: Path, advance: double, phase: double,        style: PathDashStyle): PathEffect | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | Path | 是 | 通过该路径生成一个图形，用来填充每个虚线段。 |
| advance | double | 是 | 虚线段的步长，取值范围>0，否则会抛错误码。单位为物理像素px。 |
| phase | double | 是 | 表示虚线段内图形在虚线步长范围内的偏移量，该参数为浮点数，效果为先对偏移量取绝对值，然后对步长取模。单位为物理像素px。 |
| style | [PathDashStyle](arkts-arkgraphics2d-drawing-pathdashstyle-e.md) | 是 | 指定虚线效果的样式，决定虚线段图形在路径上的变换方式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PathEffect](arkts-arkgraphics2d-drawing-patheffect-c.md) | 返回创建的虚线路径效果对象，可通过[Pen.setPathEffect]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; 3. Parameter verification failed. |

## createSumPathEffect

```TypeScript
static createSumPathEffect(firstPathEffect: PathEffect, secondPathEffect: PathEffect): PathEffect
```

创建一个叠加的路径效果。与 [createComposePathEffect](#createcomposepatheffect) 不同，此接口会分别对两个参数的效果各自独立进行表现，然后将两个效果简单重叠显示。

**起始版本：** 18

<!--Device-PathEffect-static createSumPathEffect(firstPathEffect: PathEffect, secondPathEffect: PathEffect): PathEffect--><!--Device-PathEffect-static createSumPathEffect(firstPathEffect: PathEffect, secondPathEffect: PathEffect): PathEffect-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| firstPathEffect | [PathEffect](arkts-arkgraphics2d-drawing-patheffect-c.md) | 是 | 表示第一个路径效果。 |
| secondPathEffect | [PathEffect](arkts-arkgraphics2d-drawing-patheffect-c.md) | 是 | 表示第二个路径效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PathEffect](arkts-arkgraphics2d-drawing-patheffect-c.md) | 返回创建的叠加路径效果对象，可通过[Pen.setPathEffect]{ |

## createSumPathEffect

```TypeScript
static createSumPathEffect(firstPathEffect: PathEffect, secondPathEffect: PathEffect): PathEffect | undefined
```

创建一个叠加的路径效果。与 [createComposePathEffect](#createcomposepatheffect) 不同，此接口会分别对两个参数的效果各自独立进行表现，然后将两个效果简单重叠显示。

**起始版本：** 23

<!--Device-PathEffect-static createSumPathEffect(firstPathEffect: PathEffect, secondPathEffect: PathEffect): PathEffect | undefined--><!--Device-PathEffect-static createSumPathEffect(firstPathEffect: PathEffect, secondPathEffect: PathEffect): PathEffect | undefined-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| firstPathEffect | [PathEffect](arkts-arkgraphics2d-drawing-patheffect-c.md) | 是 | 表示第一个路径效果。 |
| secondPathEffect | [PathEffect](arkts-arkgraphics2d-drawing-patheffect-c.md) | 是 | 表示第二个路径效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PathEffect](arkts-arkgraphics2d-drawing-patheffect-c.md) | 返回创建的叠加路径效果对象，可通过[Pen.setPathEffect]{ |

