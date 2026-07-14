# PathEffect

路径效果对象。

> **说明：**
>
> - 本Class首批接口从API version 12开始支持。
>
> - 本模块使用屏幕物理像素单位px。
>
> - 本模块为单线程模型策略，需要调用方自行管理线程安全和上下文状态的切换。

**起始版本：** 12

**系统能力：** SystemCapability.Graphics.Drawing

## createComposePathEffect

```TypeScript
static createComposePathEffect(outer: PathEffect, inner: PathEffect): PathEffect
```

创建路径组合的路径效果对象，首先应用内部路径效果，然后应用外部路径效果。

**起始版本：** 18

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| outer | PathEffect | 是 | 组合路径效果中外部路径效果。 |
| inner | PathEffect | 是 | 组合路径效果中内部路径效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PathEffect | 返回创建的路径效果对象。 |

## createCornerPathEffect

```TypeScript
static createCornerPathEffect(radius: number): PathEffect
```

创建将路径的夹角变成指定半径的圆角的路径效果对象。

**起始版本：** 12

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| radius | number | 是 | 圆角的半径，必须大于0，该参数为浮点数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PathEffect | 返回创建的路径效果对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

## createDashPathEffect

```TypeScript
static createDashPathEffect(intervals: Array<number>, phase: number): PathEffect
```

创建将路径变为虚线的路径效果对象。

**起始版本：** 12

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| intervals | Array&lt;number&gt; | 是 | 表示虚线的ON（实线部分）和OFF（空白部分）长度的数组，数组个数必须是偶数，且&gt;=2，该参数为正整数。 |
| phase | number | 是 | 绘制时的偏移量，该参数为浮点数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PathEffect | 返回创建的路径效果对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

## createDiscretePathEffect

```TypeScript
static createDiscretePathEffect(segLength: number, dev: number, seedAssist?: number): PathEffect
```

创建一种将路径打散，并且在路径上产生不规则分布的效果。

**起始版本：** 18

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| segLength | number | 是 | 路径中每进行一次打散操作的长度，该长度为浮点数，负数和0时无效果。 |
| dev | number | 是 | 绘制时的末端点的最大移动偏离量，该偏移量为浮点数。 |
| seedAssist | number | 否 | 生成效果伪随机种子辅助变量，默认值为0，该参数为32位无符号整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PathEffect | 返回创建的路径效果对象。 |

## createPathDashEffect

```TypeScript
static createPathDashEffect(path: Path, advance: number, phase: number, style: PathDashStyle): PathEffect
```

通过路径描述的形状创建一个虚线路径效果。

**起始版本：** 18

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | Path | 是 | 通过该路径生成一个图形，用来填充每个虚线段。 |
| advance | number | 是 | 虚线段的步长，该参数为大于0的浮点数，否则会抛错误码。 |
| phase | number | 是 | 表示虚线段内图形在虚线步长范围内的偏移量，该参数为浮点数，效果为先对偏移量取绝对值，然后对步长取模。 |
| style | PathDashStyle | 是 | 指定虚线效果的样式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PathEffect | 返回创建的路径效果对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |

## createSumPathEffect

```TypeScript
static createSumPathEffect(firstPathEffect: PathEffect, secondPathEffect: PathEffect): PathEffect
```

创建一个叠加的路径效果。与createComposePathEffect不同，此接口会分别对两个参数的效果各自独立进行表现，然后将两个效果简单重叠显示。

**起始版本：** 18

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| firstPathEffect | PathEffect | 是 | 表示第一个路径效果。 |
| secondPathEffect | PathEffect | 是 | 表示第二个路径效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| PathEffect | 返回创建的路径效果对象。 |

