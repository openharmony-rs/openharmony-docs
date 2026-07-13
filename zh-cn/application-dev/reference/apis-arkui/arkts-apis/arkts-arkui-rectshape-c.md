# RectShape

用于clipShape和maskShape接口的矩形形状。

继承自[BaseShape](arkts-arkui-baseshape-c.md)。

**继承/实现关系：** RectShape extends [BaseShape<RectShape>](BaseShape<RectShape>)

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(options?: RectShapeOptions | RoundRectShapeOptions)
```

创建RectShape对象。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | RectShapeOptions \| RoundRectShapeOptions | 否 | 矩形形状参数。 |

## radius

```TypeScript
radius(radius: number | string | Array<number | string>): RectShape
```

设置矩形形状的圆角半径。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| radius | number \| string \| Array&lt;number \| string&gt; | 是 | 矩形形状的圆角半径。仅接受数组的前四个元素，分别为矩形左上，右上，左下，右下的圆角半径。<br/> 类型为number时取值范围是[0, +∞)，string时是[Length](../arkts-components/arkts-arkui-length-t.md)。<br/>单位：vp<br/>取值为异常值时按照0vp处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RectShape | 返回RectShape对象。 |

## radiusHeight

```TypeScript
radiusHeight(rHeight: number | string): RectShape
```

设置矩形形状圆角半径的高度。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rHeight | number \| string | 是 | 矩形形状圆角半径的高度。 <br/> 类型为number时取值范围是[0, +∞)，string时是[Length](../arkts-components/arkts-arkui-length-t.md)。<br/>单位：vp<br/>取值为异常值时按照0vp处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RectShape | 返回RectShape对象。 |

## radiusWidth

```TypeScript
radiusWidth(rWidth: number | string): RectShape
```

设置矩形形状圆角半径的宽度。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rWidth | number \| string | 是 | 矩形形状圆角半径的宽度。<br/> 类型为number时取值范围是[0, +∞)，string时是[Length](../arkts-components/arkts-arkui-length-t.md)。<br/>单位：vp<br/>取值为异常值时按照0vp处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| RectShape | 返回RectShape对象。 |

