# Path

路径绘制组件，根据绘制路径生成封闭的自定义形状。

> **说明：**
>
> 该组件从API version 20开始支持使用[AttributeUpdater]{@link AttributeUpdater}类的
> [updateConstructorParams](docroot://reference/apis-arkui/js-apis-arkui-AttributeUpdater.md#属性)接口更新构造参数。

## 子组件

无

## SVG路径描述规范

SVG路径描述规范支持的命令如下：

| 命令 | 名称 | 参数 | 说明 |  
| ---- | -------------------------------- | ---------------------------------------- | ---------------------------------------- |  
| M | moveto | x：起始点的x轴坐标。</br>y：起始点的y轴坐标。 | 在给定的(x, y)坐标处开始一个新的子路径。例如，`M 0 0`表示将(0, 0)点作为新子路径的起始点。 |  
| L | lineto | x：直线终点的x轴坐标。</br>y：直线终点的y轴坐标。 | 从当前点到给定的(x, y)坐标画一条线，该坐标成为新的当前点。例如，`L 50 50`表示绘制当前点到(50, 50)点的直线，并将(50, 50)点作为新子路径的起始点。 |  
| H | horizontal lineto | x：水平直线终点的x轴坐标。 | 从当前点绘制一条水平线到给定的x坐标，等效于将y坐标指定为当前点y坐标的L命令。例如，当前点为(100, 100)，`H 50 `表示绘制当前点到(50, 100)点的直线，并将(50, 100)点作为新子路径的起始点。 |  
| V | vertical lineto | y：垂直直线终点的y轴坐标。 | 从当前点绘制一条垂直线到给定的y坐标，等效于将x坐标指定为当前点x坐标的L命令。例如，当前点为(100, 100)，`V 50 `表示绘制当前点到(100, 50)点的直线，并将(100, 50)点作为新子路径的起始点。 |  
| C | curveto | x1：第一个控制点参数的x坐标值。</br>y1：第一个控制点参数的y坐标值。</br>x2：第二个控制点参数的x坐标值。</br>y2：第二个控制点参数的y坐标值。</br>x：终点参数的x坐标值。</br>y：终点参数的y坐标值。 | 使用(x1, y1)作为曲线起点的控制点，(x2, y2)作为曲线终点的控制点，从当前点到(x, y)绘制三次贝塞尔曲线。例如，`C100 100 250 100 250 200 `表示绘制当前点到(250, 200)点的三次贝塞尔曲线，并将(250, 200)点作为新子路径的起始点。 |  
| S | smooth curveto | x2：第二个控制点参数的x坐标值。</br>y2：第二个控制点参数的y坐标值。</br>x：终点参数的x坐标值。</br>y：终点参数的y坐标值。 |(x2, y2)作为曲线终点的控制点，绘制从当前点到(x, y)绘制三次贝塞尔曲线。若前一个命令是C或S，则起点控制点是上一个命令的终点控制点相对于起点的映射。例如，`C100 100 250 100 250 200 S400 300 400 200`第二段贝塞尔曲线的起点控制点为(250, 300)。如果没有前一个命令或者前一个命令不是 C或S，则第一个控制点与当前点重合。 |  
| Q | quadratic Bezier curve | x1：第一个控制点参数的x坐标值。</br>y1：第一个控制点参数的y坐标值。</br>x：终点参数的x坐标值。</br>y：终点参数的y坐标值。 | 使用(x1, y1)作为控制点，从当前点到(x, y)绘制二次贝塞尔曲线。例如，`Q400 50 600 300 `表示绘制当前点到(600, 300)点的二次贝塞尔曲线，并将(600, 300)点作为新子路径的起始点。 |  
| T | smooth quadratic Bezier curveto | x：终点参数的x坐标值。</br>y：终点参数的y坐标值。 | 绘制从当前点到(x, y)绘制二次贝塞尔曲线。若前一个命令是Q或T，则控制点是上一个命令的终点控制点相对于起点的映射。 例如，`Q400 50 600 300 T1000 300`第二段贝塞尔曲线的控制点为(800, 350)。 如果没有前一个命令或者前一个命令不是Q或T，则第一个控制点与当前点重合。 |  
| A | elliptical Arc | rx：椭圆的x轴半径。</br>ry：椭圆的y轴半径。</br>x-axis-rotation：椭圆相对于坐标系的旋转角度。</br>large-arc-flag：标记绘制大弧(1)还是小弧(0)。</br>sweep-flag：标记向顺时针(1)还是逆时针(0)方向绘制。</br>x：终点参数的x坐标值。</br>y：终点参数的y坐标值。 | 从当前点到(x, y)绘制一条椭圆弧。椭圆的大小和方向由两个半径(rx, ry)和x-axis-rotation定义，指示整个椭圆相对于当前坐标系如何旋转（以度为单位）。 large-arc-flag 和 sweep-flag确定弧的绘制方式。 |  
| Z | closepath | none | 通过将当前路径连接回当前子路径的初始点来关闭当前子路径。 |

例如：commands('M0 20 L50 50 L50 100 Z')定义了一个三角形，起始于位置(0, 20)，接着绘制点(0, 20)到点(50, 50)的直线，再绘制从点(50, 50)到点(50, 100)的直线，最后绘制从点(50, 100)到(0, 20)的直线关闭路径，形成封闭三角形。

## Path

```TypeScript
Path(options?: PathOptions)
```

Use new to create Path.Annonymous Object Rectification.

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-PathInterface-new (options?: PathOptions): PathAttribute--><!--Device-PathInterface-new (options?: PathOptions): PathAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | PathOptions | 否 | path options |

## Path

```TypeScript
Path(options?: PathOptions)
```

用于描述Path组件绘制属性。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-PathInterface-(options?: PathOptions): PathAttribute--><!--Device-PathInterface-(options?: PathOptions): PathAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | PathOptions | 否 | Path绘制区域。<br/>异常值undefined和null按照无效值处理，本次设置不生效。 |

## 汇总

- [PathOptions](arkts-arkui-path-pathoptions-i.md)
