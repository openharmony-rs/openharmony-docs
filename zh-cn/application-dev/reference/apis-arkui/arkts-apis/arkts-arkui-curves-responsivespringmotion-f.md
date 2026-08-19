# responsiveSpringMotion

## 导入模块

```TypeScript
import { curves } from '@kit.ArkUI';
```

## responsiveSpringMotion

```TypeScript
export function responsiveSpringMotion(response?: double, dampingFraction?: double, overlapDuration?: double): ICurve
```

构造弹性跟手动画曲线对象，是springMotion的一种特例，仅默认 参数不同，可与springMotion混合使用。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-curves-export function responsiveSpringMotion(response?: double, dampingFraction?: double, overlapDuration?: double): ICurve--><!--Device-curves-export function responsiveSpringMotion(response?: double, dampingFraction?: double, overlapDuration?: double): ICurve-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| response | double | 否 | 解释同springMotion中的response。<br/>默认值：0.15<br/>单位：秒<br/>取值范围：(0, +∞)<br/>**说明：** &lt;br/ &gt;设置小于等于0的值时，按默认值0.15处理。 |
| dampingFraction | double | 否 | 解释同springMotion中的dampingFraction。<br/>默认值：0.86<br/>单位：秒<br/>取值范围： 0, +∞)<br/>**说明：** <br/>设置小于0的值时，按默认值0.86处理。 |
| overlapDuration | double | 否 | 解释同springMotion中的overlapDuration。<br/>默认值：0.25<br/>单位：秒<br/>取值范围： [0, +∞)<br/>**说明：** <br/>设置小于0的值时，按默认值0.25处理。<br/>弹性跟手动画曲线为springMotion的一种特例，仅默认值不同。如果使用自定义参数的弹性曲线，推荐使用springMotion构造曲线。如果使用跟手动画，推荐使用默认参数的弹性跟手动画曲线。<br/>[animation、animateTo、pageTransition中的duration参数不生效，动画持续时间取决于responsiveSpringMotion动画曲线参数和之前的速度，也不能通过该曲线的interpolate函数获得插值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ICurve | 曲线对象。 <br>**说明:** <br>1、弹性跟手动画曲线为springMotion的一种特例，仅默认值不同。如果使用自定义参数的弹性曲线，推荐使用springMotion构造曲线；如果使用跟手动画，推荐使用默认参数的弹性跟手动画曲线。 <br>2、[animation]{ |

