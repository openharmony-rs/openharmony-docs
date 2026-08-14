# cubicBezierCurve

## cubicBezierCurve

```TypeScript
export function cubicBezierCurve(x1: double, y1: double, x2: double, y2: double): ICurve
```

构造三阶贝塞尔曲线对象，确保曲线的值在0到1之间。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-curves-export function cubicBezierCurve(x1: double, y1: double, x2: double, y2: double): ICurve--><!--Device-curves-export function cubicBezierCurve(x1: double, y1: double, x2: double, y2: double): ICurve-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x1 | double | 是 | 确定贝塞尔曲线第一点横坐标。&lt;br/&gt;取值范围：[0, 1]&lt;br/&gt;**说明：** &lt;br/&gt;设置的值小于0时，按0处理；设置的值大于1时，按1处理。 |
| y1 | double | 是 | 确定贝塞尔曲线第一点纵坐标。&lt;br/&gt;取值范围：(-∞, +∞) |
| x2 | double | 是 | 确定贝塞尔曲线第二点横坐标。&lt;br/&gt;取值范围：[0, 1]&lt;br/&gt;**说明：** &lt;br/&gt;设置的值小于0时，按0处理；设置的值大于1时，按1处理。 |
| y2 | double | 是 | 确定贝塞尔曲线第二点纵坐标。&lt;br/&gt;取值范围：(-∞, +∞) |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ICurve | 曲线的插值对象。 |

