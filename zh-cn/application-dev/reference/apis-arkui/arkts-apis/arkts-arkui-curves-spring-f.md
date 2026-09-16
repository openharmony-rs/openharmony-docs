# spring

## 导入模块

```TypeScript
import { curves } from '@kit.ArkUI';
```

## spring

```TypeScript
function spring(velocity: number, mass: number, stiffness: number, damping: number): string
```

构造弹簧曲线对象，曲线形状由弹簧参数决定，动画时长受animation、animateTo中的duration参数控制。与[interpolatingSpring](arkts-arkui-curves-interpolatingspring-f.md)相比，两者参数签名相同但行为不同：springCurve适用于需要固定动画时长的弹簧动画场景；interpolatingSpring适用于由弹簧参数自然决定动画时长的物理弹簧动画场景。

> **说明：** 
> 
> 从API version 7开始支持，从API version 9开始废弃。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [springCurve](arkts-arkui-curves-springcurve-f.md)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| velocity | number | 是 | 初始速度。外部因素对弹性动效产生的影响参数，目的是保证对象从之前的运动状态平滑地过渡到弹性动效。该速度是归一化速度，其值等于动画开始时的实际速度除以动画属性改变值。<br>取值范围：(-∞, +∞) |
| mass | number | 是 | 质量。弹性系统的受力对象，会对弹性系统产生惯性影响。质量越大，震荡的幅度越大，恢复到平衡位置的速度越慢。<br>取值范围：(0, +∞) <br>**说明：** <br>设置的值小于等于0时，按1处理。 |
| stiffness | number | 是 | 刚度。物体抵抗施加的力而形变的程度。在弹性系统中，刚度越大，抵抗变形的能力越强，恢复到平衡位置的速度就越快。<br>取值范围：(0, +∞) <br>**说明：** <br>设置的值小于等于0时，按1处理。 |
| damping | number | 是 | 阻尼。弹性系统中的阻尼系数，用于描述系统在受到扰动后震荡及衰减的情形。阻尼越大，弹性运动的震荡次数越少、震荡幅度越小。<br>取值范围：(0, +∞) <br>**说明：** <br>设置的值小于等于0时，按1处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回弹簧曲线对象。 |
