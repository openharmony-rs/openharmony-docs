# RectShape

用于clipShape和maskShape接口的矩形形状。 继承自[BaseShape](arkts-arkui-arkui-shape-baseshape-c.md)。

**继承/实现关系：** RectShape extends [BaseShape](arkts-arkui-arkui-shape-baseshape-c.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class RectShape--><!--Device-unnamed-export declare class RectShape-End-->

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

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RectShape-constructor(options?: RectShapeOptions | RoundRectShapeOptions)--><!--Device-RectShape-constructor(options?: RectShapeOptions | RoundRectShapeOptions)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [RectShapeOptions](arkts-arkui-arkui-shape-rectshapeoptions-i.md) \| [RoundRectShapeOptions](arkts-arkui-arkui-shape-roundrectshapeoptions-i.md) | 否 | 矩形形状参数。 |

## radius

```TypeScript
radius(radius: double | string | Array<double | string>): this
```

设置矩形形状的圆角半径。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RectShape-radius(radius: double | string | Array<double | string>): this--><!--Device-RectShape-radius(radius: double | string | Array<double | string>): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| radius | double \| string \| Array&lt;double \| string&gt; | 是 | Array&lt;double |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | 返回RectShape对象。 |

## radiusHeight

```TypeScript
radiusHeight(rHeight: double | string): this
```

设置矩形形状圆角半径的高度。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RectShape-radiusHeight(rHeight: double | string): this--><!--Device-RectShape-radiusHeight(rHeight: double | string): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rHeight | double \| string | 是 | 矩形形状圆角半径的高度。 <br/> 类型为number时取值范围是 0, +∞)，类型为string时是[Length。<br/>单位：vp<br/>取值为异常值时按照0vp处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | 返回RectShape对象。 |

## radiusWidth

```TypeScript
radiusWidth(rWidth: double | string): this
```

设置矩形形状圆角半径的宽度。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RectShape-radiusWidth(rWidth: double | string): this--><!--Device-RectShape-radiusWidth(rWidth: double | string): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rWidth | double \| string | 是 | 矩形形状圆角半径的宽度。<br/> 类型为double时取值范围是 0, +∞)，类型为string时是[Length。<br/>单位：vp<br/>取值为异常值时按照0vp处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | 返回当前对象。 |

