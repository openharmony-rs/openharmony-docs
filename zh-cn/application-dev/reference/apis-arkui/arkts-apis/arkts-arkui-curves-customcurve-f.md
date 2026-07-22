# customCurve

## 导入模块

```TypeScript
import { curves } from '@kit.ArkUI';
```

## customCurve

```TypeScript
function customCurve(interpolate: (fraction: number) => number): ICurve
```

构造自定义曲线对象。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-curves-function customCurve(interpolate: (fraction: number) => number): ICurve--><!--Device-curves-function customCurve(interpolate: (fraction: number) => number): ICurve-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| interpolate | (fraction: number) =&gt; number | 是 | 用户自定义的插值回调函数。<br/>fraction为动画开始时的插值输入x值。取值范围：[0,1]<br/>返回值为曲线的y值。取值范围：[0,1]<br />**说明：**<br />fraction等于0时，返回值为0对应动画起点，返回不为0，动画在起点处有跳变效果。<br/>fraction等于1时，返回值为1对应动画终点，返回值不为1将导致动画的终值不是状态变量的值，出现大于或者小于状态变量值，再跳变到状态变量值的效果。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ICurve](../arkts-components/arkts-arkui-icurve-i.md) | 曲线的插值对象。 |

**示例：**

```TypeScript
import { curves } from '@kit.ArkUI';
let interpolate = (fraction: number): number => {
  return Math.sqrt(fraction);
};
let curve = curves.customCurve(interpolate); // 创建一个用户自定义插值曲线

```

