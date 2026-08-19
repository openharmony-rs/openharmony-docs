# ICurve

曲线对象，支持通过本模块中的 curves.cubicBezierCurve、 curves.interpolatingSpring等 方法创建不同类型的曲线对象，并可通过曲线对象调用其interpolate的成员方法。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-curves-export interface ICurve--><!--Device-curves-export interface ICurve-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { curves } from '@kit.ArkUI';
```

## interpolate

```TypeScript
interpolate(fraction: double): double
```

插值曲线的插值计算函数，可以通过传入的归一化时间参数返回当前的插值。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ICurve-interpolate(fraction: double): double--><!--Device-ICurve-interpolate(fraction: double): double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fraction | double | 是 | 当前的归一化时间参数。<br/>取值范围：[0,1]<br/>**说明：** <br/>设置的值小于0时，按0处理；设置的值大于1时，按1处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double | 返回归一化time时间点对应的曲线插值。 |

