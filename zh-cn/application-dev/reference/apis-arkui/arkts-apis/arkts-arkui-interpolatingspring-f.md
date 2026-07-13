# interpolatingSpring

## interpolatingSpring

```TypeScript
function interpolatingSpring(velocity: number, mass: number, stiffness: number, damping: number): ICurve
```

构造插值器弹簧曲线对象，生成一条从0到1的动画曲线，实际动画值根据曲线进行插值计算。动画时间由曲线参数决定，不受animation、animateTo中的duration参数控制。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| velocity | number | 是 | Initial velocity. It is applied by external factors to the spring animation,designed to help ensure the smooth transition from the previous motion state.The velocity is the normalized velocity, and its value is equal to the actual velocity at the beginning ofthe animation divided by the animation attribute change value.<br>Value range: (-∞, +∞). |
| mass | number | 是 | Mass, which influences the inertia in the spring system. The greater the mass,the greater the amplitude of the oscillation, and the slower the speed of restoring to the equilibriumposition.<br>Value range: (0, +∞).&lt;p&gt;**NOTE**:<br>If this parameter is set to a value less than or equal to 0, the value **1** is used.&lt;/p&gt; |
| stiffness | number | 是 | Stiffness. It is the degree to which an object deforms by resistingthe force applied. In an elastic system, the greater the stiffness, the stronger the ability to resistdeformation, and the faster the speed of restoring to the equilibrium position.<br>Value range: (0, +∞).&lt;p&gt;**NOTE**:<br>If this parameter is set to a value less than or equal to 0, the value **1** is used.&lt;/p&gt; |
| damping | number | 是 | Damping. It is used to describe the oscillation and attenuation of the systemafter being disturbed. The larger the damping, the smaller the number of oscillations of elastic motion,and the smaller the oscillation amplitude.<br>Value range: (0, +∞)<br>&lt;p&gt;**NOTE**:<br>If this parameter is set to a value less than or equal to 0, the value **1** is used.&lt;/p&gt; |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ICurve | 曲线对象。<br>**说明:** 弹性动画曲线为物理曲线，[animation](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)、[animateTo](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)、[pageTransition](../arkts-components/arkts-arkui-pagetransitionenter.md)中的duration参数不生效，动画持续时间取决于interpolatingSpring动画曲线参数。时间不能归一，故不能通过该曲线的[interpolate](arkts-arkui-icurve-i.md#interpolate-1)函数获得插值。 |

**示例：**

```TypeScript
import { curves } from '@kit.ArkUI'
curves.interpolatingSpring(10, 1, 228, 30) // 创建一个时长由弹簧参数决定的弹簧插值曲线

```

