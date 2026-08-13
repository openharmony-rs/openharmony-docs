# stepsCurve

## stepsCurve

```TypeScript
export function stepsCurve(count: int, end: boolean): ICurve
```

构造阶梯曲线对象。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-curves-export function stepsCurve(count: int, end: boolean): ICurve--><!--Device-curves-export function stepsCurve(count: int, end: boolean): ICurve-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| count | int | 是 | 阶梯的数量，需要为正整数。&lt;br/&gt;取值范围：[1, +∞)&lt;br/&gt;**说明：** &lt;br/&gt;设置小于1的值时，按值为1处理。 |
| end | boolean | 是 | 在每个间隔的起点或终点发生阶跃变化。&lt;br&gt;-true：在终点发生阶跃变化。&lt;br&gt;-false：在起点发生阶跃变化。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ICurve | 曲线的插值对象。 |

