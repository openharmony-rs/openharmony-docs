# ICurve

曲线对象，支持通过本模块中的[curves.initCurve](arkts-arkui-curves-initcurve-f.md)、[curves.stepsCurve](arkts-arkui-curves-stepscurve-f.md)、[curves.cubicBezierCurve](arkts-arkui-curves-cubicbeziercurve-f.md)、[curves.springCurve](arkts-arkui-curves-springcurve-f.md)、[curves.springMotion](arkts-arkui-curves-springmotion-f.md)、[curves.responsiveSpringMotion](arkts-arkui-curves-responsivespringmotion-f.md)、[curves.interpolatingSpring](arkts-arkui-curves-interpolatingspring-f.md)、[curves.customCurve](arkts-arkui-curves-customcurve-f.md)方法创建不同类型的曲线对象，并可通过曲线对象调用其[interpolate](#interpolate)的成员方法。其中springMotion、responsiveSpringMotion、interpolatingSpring创建的弹性动画曲线为物理曲线，时间不能归一，不能通过interpolate函数获得插值。

**起始版本：** 9

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { curves } from '@kit.ArkUI';
```

## interpolate

```TypeScript
interpolate(fraction : number) : number
```

插值曲线的插值计算函数，可以通过传入的归一化时间参数返回当前的插值。对于springMotion、responsiveSpringMotion、interpolatingSpring等物理曲线，时间不能归一化，调用interpolate函数无法获得有效插值。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fraction | number | 是 | 当前的归一化时间参数。<br>取值范围：[0,1] <br>**说明：** <br>设置的值小于0时，按0处理；设置的值大于1时，按1处理。<br>对于springMotion、responsiveSpringMotion、interpolatingSpring创建的弹性动画曲线，时间不能归一，此参数无意义，不能通过interpolate函数获得有效插值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回归一化时间点对应的曲线插值。 |

**示例**

```TypeScript
import { curves } from '@kit.ArkUI'
let curveValue = curves.initCurve(Curve.EaseIn); // 创建一个默认先慢后快插值曲线
let interpolatedValue: number = curveValue.interpolate(0.5); // 计算得到时间到一半时的插值
```
