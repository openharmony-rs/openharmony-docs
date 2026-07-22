# spring

## 导入模块

```TypeScript
import { curves } from '@kit.ArkUI';
```

## spring

```TypeScript
function spring(velocity: number, mass: number, stiffness: number, damping: number): string
```

构造弹簧曲线对象。
> **说明：**  
>  
> 从API version 7开始支持，从API version 9开始废弃。建议使用[Curves.springCurve](arkts-arkui-curves-springcurve-f.md#springcurve)替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [springCurve](arkts-arkui-curves-springcurve-f.md#springcurve)

<!--Device-curves-function spring(velocity: number, mass: number, stiffness: number, damping: number): string--><!--Device-curves-function spring(velocity: number, mass: number, stiffness: number, damping: number): string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| velocity | number | 是 | 初始速度。是由外部因素对弹性动效产生的影响参数，其目的是保证对象从之前的运动状态平滑地过渡到弹性动效。 |
| mass | number | 是 | 质量。弹性系统的受力对象，会对弹性系统产生惯性影响。质量越大，震荡的幅度越大，恢复到平衡位置的速度越慢。 |
| stiffness | number | 是 | 刚度。是物体抵抗施加的力而形变的程度。在弹性系统中，刚度越大，抵抗变形的能力越强，恢复到平衡位置的速度就越快。 |
| damping | number | 是 | 阻尼。是一个纯数，无真实的物理意义，用于描述系统在受到扰动后震荡及衰减的情形。阻尼越大，弹性运动的震荡次数越少、震荡幅度越小。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回弹簧曲线对象。 |

