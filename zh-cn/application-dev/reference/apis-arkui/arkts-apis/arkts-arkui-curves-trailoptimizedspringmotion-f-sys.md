# trailOptimizedSpringMotion（系统接口）

## 导入模块

```TypeScript
import { curves } from '@kit.ArkUI';
```

## trailOptimizedSpringMotion

```TypeScript
function trailOptimizedSpringMotion(response?: number, dampingFraction?: number, overlapDuration?: number, trail?: TrailOptimization): ICurve
```

在[springMotion](arkts-arkui-curves-springmotion-f.md)基础上新增尾迹优化参数，构造带尾迹优化的弹性动画曲线对象。如果对同一对象的同一属性进行多个弹性动画，每个动画会替换掉前一个动画，并继承之前的速度。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| response | number | 否 | 弹簧自然振动周期，决定弹簧复位的速度。<br>默认值：0.55<br>单位：秒<br>取值范围：(0, +∞)<br>**说明：** <br>设置小于等于0的值时，按默认值0.55处理。 |
| dampingFraction | number | 否 | 阻尼系数。<br>0表示无阻尼，一直处于震荡状态；<br>大于0小于1的值为欠阻尼，运动过程中会超出目标值；<br>等于1为临界阻尼；<br>大于1为过阻尼，运动过程中逐渐趋于目标值。<br>默认值：0.825<br>取值范围：0, +∞)<br>**说明：** <br>设置小于0的值时，按默认值0.825处理。 |
| overlapDuration | number | 否 | 弹性动画衔接时长。发生动画继承时，如果前后两个弹性动画response不一致，response参数会在overlapDuration时间内平滑过渡。<br>默认值：0<br>单位：秒<br>取值范围：[0, +∞)<br>**说明：** <br>设置小于0的值时，按默认值0处理。<br>弹性动画曲线为物理曲线，[animation、animateTo、pageTransition中的duration参数不生效，动画持续时间取决于trailOptimizedSpringMotion动画曲线参数和之前的速度。时间不能归一，故不能通过该曲线的interpolate函数获得插值。 |
| trail | [TrailOptimization](arkts-arkui-curves-trailoptimization-i-sys.md) | 否 | 尾迹优化配置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ICurve](arkts-arkui-curves-icurve-i.md) | 曲线对象。<br>**说明：** <br>弹性动画曲线为物理曲线，animation、animateTo、pageTransition中的duration参数不生效，动画持续时间取决于trailOptimizedSpringMotion动画曲线参数和之前的速度。时间不能归一，故不能通过该曲线的[interpolate](arkts-arkui-curves-icurve-i.md#interpolate)函数获得插值。 |
