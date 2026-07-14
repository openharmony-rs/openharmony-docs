# cubicBezier

## cubicBezier

```TypeScript
function cubicBezier(x1: number, y1: number, x2: number, y2: number): string
```

构造三阶贝塞尔曲线对象，曲线的值必须处于0-1之间。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃。建议使用[Curves.cubicBezierCurve](arkts-arkui-cubicbeziercurve-f.md#cubicbeziercurve-1)替代。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [cubicBezierCurve](arkts-arkui-cubicbeziercurve-f.md#cubicbeziercurve-1)

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| x1 | number | 是 | -Value range [0, 1]. |
| y1 | number | 是 | -Value range (-∞, +∞). |
| x2 | number | 是 | -Value range [0, 1]. |
| y2 | number | 是 | -Value range (-∞, +∞). |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回三阶贝塞尔曲线对象。 |

