# springCurve

## 导入模块

```TypeScript
import { curves } from '@kit.ArkUI';
```

## springCurve

```TypeScript
export function springCurve(velocity: double, mass: double, stiffness: double, damping: double): ICurve
```

构造弹簧曲线对象，曲线形状由弹簧参数决定，动画时长受animation、animateTo中的duration参数控制。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-curves-export function springCurve(velocity: double, mass: double, stiffness: double, damping: double): ICurve--><!--Device-curves-export function springCurve(velocity: double, mass: double, stiffness: double, damping: double): ICurve-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| velocity | double | 是 | Initial velocity. It is applied by external factors to the spring animation, designed to help ensure the smooth transition from the previous motion state. The velocity is the normalized velocity, and its value is equal to the actual velocity at the beginning of the animation divided by the animation attribute change value. Value range: (-∞, +∞). |
| mass | double | 是 | Mass which influences the inertia in the spring system. The greater the mass, the greater the amplitude of the oscillation, and the slower the speed of restoring to the equilibrium position. Value range: (0, +∞). &lt;p&gt;**NOTE：**: <br>If this parameter is set to a value less than or equal to 0, the value 1 is used. &lt;/p&gt; |
| stiffness | double | 是 | Stiffness. It is the degree to which an object deforms by resisting the force applied. In an elastic system, the greater the stiffness, the stronger the ability to resist deformation, and the faster the speed of restoring to the equilibrium position.Value range: (0, +∞). &lt;p&gt;**NOTE：**: <br>If this parameter is set to a value less than or equal to 0, the value 1 is used. &lt;/p&gt; |
| damping | double | 是 | Damping. It is used to describe the oscillation and attenuation of the system after being disturbed. The larger the damping, the smaller the number of oscillations of elastic motion, and the smaller the oscillation amplitude.Value range: (0, +∞). &lt;p&gt;**NOTE：**: <br>If this parameter is set to a value less than or equal to 0, the value 1 is used. &lt;/p&gt; |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ICurve | 曲线的插值对象。 |

