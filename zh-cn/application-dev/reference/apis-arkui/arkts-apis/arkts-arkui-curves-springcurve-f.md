# springCurve

## 导入模块

```TypeScript
import { curves } from '@kit.ArkUI';
```

<a id="springcurve"></a>
## springCurve

```TypeScript
function springCurve(velocity: number, mass: number, stiffness: number, damping: number): ICurve
```

构造弹簧曲线对象，曲线形状由弹簧参数决定，动画时长受animation、animateTo中的duration参数控制。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-curves-function springCurve(velocity: number, mass: number, stiffness: number, damping: number): ICurve--><!--Device-curves-function springCurve(velocity: number, mass: number, stiffness: number, damping: number): ICurve-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| velocity | number | 是 | Initial velocity. It is applied by external factors to the spring animation,designed to help ensure the smooth transition from the previous motion state. The velocity is the normalized velocity, and its value is equal to the actual velocity at the beginning of the animation divided by the animation attribute change value.Value range: (-∞, +∞). |
| mass | number | 是 | Mass, which influences the inertia in the spring system. The greater the mass,the greater the amplitude of the oscillation, and the slower the speed of restoring to the equilibrium position.Value range: (0, +∞).<p>**NOTE**:<br>If this parameter is set to a value less than or equal to 0, the value 1 is used.</p> |
| stiffness | number | 是 | Stiffness.It is the degree to which an object deforms by resisting the force applied. In an elastic system, the greater the stiffness, the stronger the ability to resist deformation,and the faster the speed of restoring to the equilibrium position.Value range: (0, +∞).<p>**NOTE**:<br>If this parameter is set to a value less than or equal to 0, the value 1 is used.</p> |
| damping | number | 是 | -Damping. It is used to describe the oscillation and attenuation of the system |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ICurve](../arkts-components/arkts-arkui-icurve-i.md) | 曲线的插值对象。 |

**示例：**

```TypeScript
import { curves } from '@kit.ArkUI';
curves.springCurve(10, 1, 228, 30); // 创建一个弹簧插值曲线

```

