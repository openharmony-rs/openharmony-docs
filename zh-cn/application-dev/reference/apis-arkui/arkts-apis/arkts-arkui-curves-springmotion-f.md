# springMotion

## 导入模块

```TypeScript
import { curves } from '@kit.ArkUI';
```

## springMotion

```TypeScript
function springMotion(response?: number, dampingFraction?: number, overlapDuration?: number): ICurve
```

构造弹性动画曲线对象。与使用弹簧物理参数的[curves.springCurve](arkts-arkui-curves-springcurve-f.md)不同，springMotion使用响应式参数构造曲线，且支持动画间的速度继承，需要速度继承的连续弹性动画建议使用springMotion。如果对同一对象的同一属性进行多个弹性动画，每个动画会替换掉前一个动画，并继承之前的速度。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| response | number | 否 | 弹簧自然振动周期，决定弹簧复位的速度。<br>默认值：0.55 <br>单位：秒<br>取值范围：(0, +∞) <br>**说明：** <br>设置小于等于0的值时，按默认值0.55处理。 |
| dampingFraction | number | 否 | 阻尼系数。<br>0表示无阻尼，一直处于震荡状态；<br>大于0小于1的值为欠阻尼，运动过程中会超出目标值；<br>等于1为临界阻尼；<br>大于1为过阻尼，运动过程中逐渐趋于目标值。<br>默认值：0.825 <br>取值范围：0, +∞) <br>**说明：** <br>设置小于0的值时，按默认值0.825处理。 |
| overlapDuration | number | 否 | 弹性动画衔接时长。发生动画继承时，如果前后两个弹性动画response不一致，response参数会在overlapDuration时间内平滑过渡；当overlapDuration为0时，response参数不会进行平滑过渡，而是立即切换到新的response值。<br>默认值：0 <br>单位：秒<br>取值范围：[0, +∞) <br> **说明：** <br>设置小于0的值时，按默认值0处理。<br>弹性动画曲线为物理曲线，[animation、animateTo、pageTransition中的duration参数不生效，动画持续时间取决于springMotion动画曲线参数和之前的速度。时间不能归一，故不能通过该曲线的interpolate函数获得插值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ICurve](arkts-arkui-curves-icurve-i.md) | 曲线对象。<br>**说明：** <br>弹性动画曲线为物理曲线，animation、animateTo、pageTransition中的duration参数不生效，动画持续时间取决于springMotion动画曲线参数和之前的速度。时间不能归一，故不能通过该曲线的[interpolate](arkts-arkui-curves-icurve-i.md#interpolate)函数获得插值。 |

**示例**

```TypeScript
import { curves } from '@kit.ArkUI';
curves.springMotion(); // 创建一个默认弹性动画曲线
curves.springMotion(0.5); // 创建指定response、其余参数默认的弹性动画曲线
curves.springMotion(0.5, 0.6); // 创建指定response和dampingFraction、其余参数默认的弹性动画曲线
curves.springMotion(0.5, 0.6, 0); // 创建三个参数均自定义的弹性动画曲线
```
