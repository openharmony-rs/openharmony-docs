# responsiveSpringMotion

## responsiveSpringMotion

```TypeScript
export function responsiveSpringMotion(response?: double, dampingFraction?: double, overlapDuration?: double): ICurve
```

构造弹性跟手动画曲线对象，是springMotion的一种特例，仅默认 参数不同，可与springMotion混合使用。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-curves-export function responsiveSpringMotion(response?: double, dampingFraction?: double, overlapDuration?: double): ICurve--><!--Device-curves-export function responsiveSpringMotion(response?: double, dampingFraction?: double, overlapDuration?: double): ICurve-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| response | double | 否 | 解释同springMotion中的response。&lt;br/&gt;默认值：0.15&lt;br/&gt;单位：秒&lt;br/&gt;取值范围：(0, +∞)&lt;br/&gt;**说明：** &lt;br/ &gt;设置小于等于0的值时，按默认值0.15处理。 |
| dampingFraction | double | 否 | 解释同springMotion中的dampingFraction。&lt;br/&gt;默认值：0.86&lt;br/&gt;单位：秒&lt;br/&gt;取值范围： 0, +∞)&lt;br/&gt;**说明：** &lt;br/&gt;设置小于0的值时，按默认值0.86处理。 |
| overlapDuration | double | 否 | 解释同springMotion中的overlapDuration。&lt;br/&gt;默认值：0.25&lt;br/&gt;单位：秒&lt;br/&gt;取值范围： [0, +∞)&lt;br/&gt;**说明：** &lt;br/&gt;设置小于0的值时，按默认值0.25处理。&lt;br/&gt;弹性跟手动画曲线为springMotion的一种特例，仅默认值不同。如果使用自定义参数的弹性曲线，推荐使用springMotion构造曲线。如果使用跟手动画，推荐使用默认参数的弹性跟手动画曲线。&lt;br/&gt;[animation、animateTo、pageTransition中的duration参数不生效，动画持续时间取决于responsiveSpringMotion动画曲线参数和之前的速度，也不能通过该曲线的interpolate函数获得插值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ICurve | 曲线对象。 &lt;br&gt;**说明:** &lt;br&gt;1、弹性跟手动画曲线为springMotion的一种特例，仅默认值不同。如果使用自定义参数的弹性曲线，推荐使用springMotion构造曲线；如果使用跟手动画，推荐使用默认参数的弹性跟手动画曲线。 &lt;br&gt;2、[animation]{ |

