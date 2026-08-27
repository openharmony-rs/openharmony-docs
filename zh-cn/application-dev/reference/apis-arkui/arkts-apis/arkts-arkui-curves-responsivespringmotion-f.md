# responsiveSpringMotion

## 导入模块

```TypeScript
import { curves } from '@kit.ArkUI';
```

## responsiveSpringMotion

```TypeScript
function responsiveSpringMotion(response?: number, dampingFraction?: number, overlapDuration?: number): ICurve
```

构造弹性跟手动画曲线对象，是[springMotion](arkts-arkui-curves-springmotion-f.md)的一种特例，仅默认参数不同，可与springMotion混合使用。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| response | number | 否 | 解释同springMotion中的response。默认值：0.15单位：秒取值范围：(0, +∞)   **说明：** 设 置小于等于0的值时，按默认值0.15处理。 |
| dampingFraction | number | 否 | 解释同springMotion中的dampingFraction。默认值：0.86单位：秒取值范围： 0, +∞)   **说明：** 设置小于0的值时，按默认值0.86处理。 |
| overlapDuration | number | 否 | 解释同springMotion中的overlapDuration。默认值：0.25单位：秒取值范围： [0, +∞)   **说明：** 设置小于0的值时，按默认值0.25处理。弹性跟手动画曲线为springMotion的一种特例，仅默认值不同。如果使用自定义参数的弹性曲线，推荐使用springMotion构造曲线。如果使用跟手动画，推荐使用默认参数的弹性跟手动画曲线。 [animation、animateTo、pageTransition中的duration参数不生效，动画持续时间取决于responsiveSpringMotion动画曲线参数和之前的速度，也不能通过该曲线的interpolate函数获得插值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ICurve | 曲线对象。 |

**示例**

```TypeScript
import { curves } from '@kit.ArkUI';
curves.responsiveSpringMotion(); // 创建一个默认弹性跟手动画曲线
```
