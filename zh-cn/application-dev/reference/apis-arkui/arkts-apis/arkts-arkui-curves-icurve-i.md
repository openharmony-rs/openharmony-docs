# ICurve

曲线对象，支持通过本模块中的[curves.cubicBezierCurve](arkts-arkui-curves-cubicbeziercurve-f.md#cubicbeziercurve)、[curves.interpolatingSpring](arkts-arkui-curves-interpolatingspring-f.md#interpolatingspring)等方法创建不同类型的曲线对象，并可通过曲线对象调用其[interpolate](arkts-arkui-curves-icurve-i.md#interpolate)的成员方法。

**起始版本：** 9

<!--Device-curves-interface ICurve--><!--Device-curves-interface ICurve-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { curves } from '@kit.ArkUI';
```

## interpolate

```TypeScript
interpolate(fraction : number) : number
```

插值曲线的插值计算函数，可以通过传入的归一化时间参数返回当前的插值

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ICurve-interpolate(fraction : number) : number--><!--Device-ICurve-interpolate(fraction : number) : number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fraction | number | 是 | 当前的归一化时间参数。<br/>取值范围：[0,1]<br/>**说明：** <br/>设置的值小于0时，按0处理；设置的值大于1时，按1处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回归一化time时间点对应的曲线插值。 |

**示例：**

```TypeScript
import { curves } from '@kit.ArkUI'
let curveValue = curves.initCurve(Curve.EaseIn); // 创建一个默认先慢后快插值曲线
let interpolatedValue: number = curveValue.interpolate(0.5); // 计算得到时间到一半时的插值

```

