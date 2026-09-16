# RectShape

用于clipShape和maskShape接口的矩形形状。

继承自[BaseShape](arkts-arkui-arkui-shape-baseshape-c.md)。

**继承/实现关系：** RectShape extends BaseShape<RectShape>

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { RectShape, CircleShape, EllipseShape, PathShape } from '@kit.ArkUI';
```

## constructor

```TypeScript
constructor(options?: RectShapeOptions | RoundRectShapeOptions)
```

创建RectShape对象。

> **说明：** 
> 
> - 构造函数参数中的radius/radiusWidth/radiusHeight与radius()/radiusWidth()/radiusHeight()方法设置的是同一属性。
> 
> - 方法调用会覆盖构造函数中设置的对应属性值。
> 
> - 建议优先通过构造函数设置初始参数，再通过方法进行额外配置或覆盖。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [RectShapeOptions](arkts-arkui-arkui-shape-rectshapeoptions-i.md) &#124; [RoundRectShapeOptions](arkts-arkui-arkui-shape-roundrectshapeoptions-i.md) | 否 | 矩形形状参数。不传入时使用默认尺寸，默认宽度0vp，默认高度0vp，圆角半径默认值0vp。 |

## radius

```TypeScript
radius(radius: number | string | Array<number | string>): RectShape
```

设置矩形形状的圆角半径，设置后各角圆弧宽高相等（圆形弧）。与radiusWidth/radiusHeight分别设置圆弧宽高（允许椭圆弧）不同，radius可通过数组分别指定四个角的圆角半径值；需要圆形圆角时使用radius，需要椭圆形圆角时使用radiusWidth和radiusHeight。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| radius | number &#124; string &#124; Array&lt;number &#124; string&gt; | 是 | 矩形形状的圆角半径。仅接受数组的前四个元素，分别为矩形左上、右上、左下、右下的圆角半径。<br> 类型为number时取值范围是[0, +∞)，string时是[Length](arkts-arkui-length-t.md)。<br>单位：vp <br>取值为异常值时按照0vp处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RectShape](arkts-arkui-arkui-shape-rectshape-c.md) | 返回设置圆角半径宽度后的RectShape对象，可用于链式调用继续配置矩形形状。 |

## radiusHeight

```TypeScript
radiusHeight(rHeight: number | string): RectShape
```

设置矩形形状圆角半径的高度。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rHeight | number &#124; string | 是 | 矩形形状圆角半径的高度。<br> 类型为number时取值范围是[0, +∞)，string时是[Length](arkts-arkui-length-t.md)。<br>单位：vp <br>取值为异常值时按照0vp处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RectShape](arkts-arkui-arkui-shape-rectshape-c.md) | 返回设置圆角半径高度后的RectShape对象，可用于链式调用继续配置矩形形状。 |

## radiusWidth

```TypeScript
radiusWidth(rWidth: number | string): RectShape
```

设置矩形形状圆角半径的宽度。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rWidth | number &#124; string | 是 | 矩形形状圆角半径的宽度。<br> 类型为number时取值范围是[0, +∞)，string时是[Length](arkts-arkui-length-t.md)。<br>单位：vp <br>取值为异常值时按照0vp处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RectShape](arkts-arkui-arkui-shape-rectshape-c.md) | 返回设置圆角半径后的RectShape对象，可用于链式调用继续配置矩形形状。 |
