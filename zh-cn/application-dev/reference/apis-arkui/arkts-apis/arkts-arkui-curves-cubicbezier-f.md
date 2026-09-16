# cubicBezier

## 导入模块

```TypeScript
import { curves } from '@kit.ArkUI';
```

## cubicBezier

```TypeScript
function cubicBezier(x1: number, y1: number, x2: number, y2: number): string
```

构造三阶贝塞尔曲线对象，曲线的两个控制点横坐标x1、x2的取值范围限定在0到1之间。

> **说明：** 
> 
> 从API version 7开始支持，从API version 9开始废弃。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [cubicBezierCurve](arkts-arkui-curves-cubicbeziercurve-f.md)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x1 | number | 是 | 确定贝塞尔曲线第一点横坐标。<br>取值范围：[0, 1] <br>**说明：** <br>设置的值小于0时，按0处理；设置的值大于1时，按1处理。 |
| y1 | number | 是 | 确定贝塞尔曲线第一点纵坐标。<br>取值范围：(-∞, +∞) |
| x2 | number | 是 | 确定贝塞尔曲线第二点横坐标。<br>取值范围：[0, 1] <br>**说明：** <br>设置的值小于0时，按0处理；设置的值大于1时，按1处理。 |
| y2 | number | 是 | 确定贝塞尔曲线第二点纵坐标。<br>取值范围：(-∞, +∞) |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回三阶贝塞尔曲线对象。 |
