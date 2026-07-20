# cubicBezierCurve

## 导入模块

```TypeScript
import { curves } from '@kit.ArkUI';
```

<a id="cubicbeziercurve"></a>
## cubicBezierCurve

```TypeScript
function cubicBezierCurve(x1: number, y1: number, x2: number, y2: number): ICurve
```

构造三阶贝塞尔曲线对象，确保曲线的值在0到1之间。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-curves-function cubicBezierCurve(x1: number, y1: number, x2: number, y2: number): ICurve--><!--Device-curves-function cubicBezierCurve(x1: number, y1: number, x2: number, y2: number): ICurve-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x1 | number | 是 | 确定贝塞尔曲线第一点横坐标。<br/>取值范围：[0, 1]<br/>**说明：** <br/>设置的值小于0时，按0处理；设置的值大于1时，按1处理。 |
| y1 | number | 是 | 确定贝塞尔曲线第一点纵坐标。<br/>取值范围：(-∞, +∞) |
| x2 | number | 是 | 确定贝塞尔曲线第二点横坐标。<br/>取值范围：[0, 1]<br/>**说明：** <br/>设置的值小于0时，按0处理；设置的值大于1时，按1处理。 |
| y2 | number | 是 | 确定贝塞尔曲线第二点纵坐标。<br/>取值范围：(-∞, +∞) |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ICurve](../arkts-components/arkts-arkui-icurve-i.md) | 曲线的插值对象。 |

**示例：**

```TypeScript
import { curves } from '@kit.ArkUI';
curves.cubicBezierCurve(0.1, 0.0, 0.1, 1.0); // 创建一个三阶贝塞尔曲线

```

