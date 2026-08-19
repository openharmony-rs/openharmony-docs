# customCurve

## 导入模块

```TypeScript
import { curves } from '@kit.ArkUI';
```

## customCurve

```TypeScript
export function customCurve(interpolate: (fraction: double) => double): ICurve
```

构造自定义曲线对象。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-curves-export function customCurve(interpolate: (fraction: double) => double): ICurve--><!--Device-curves-export function customCurve(interpolate: (fraction: double) => double): ICurve-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| interpolate | (fraction: double) =&gt; double | 是 | 用户自定义的插值回调函数。<br/>fraction为动画开始时的插值输入x值。取值范围：[0,1]<br/>返回值为曲线的y值。取值范围：[0,1]&lt;br /&gt;**说明：**&lt;br /&gt;fraction等于0时，返回值为0对应动画起点，返回不为0，动画在起点处有跳变效果。<br/>fraction等于1时，返回值为1对应动画终点，返回值不为1将导致动画的终值不是状态变量的 值，出现大于或者小于状态变量值，再跳变到状态变量值的效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ICurve | 曲线的插值对象。 |

