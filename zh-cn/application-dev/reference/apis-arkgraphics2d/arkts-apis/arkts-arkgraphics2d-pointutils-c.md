# PointUtils

This class offers a comprehensive set of operations for handling common2D Point objects.

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Graphics.Drawing

## negate

```TypeScript
static negate(point: common2D.Point): void
```

取反点的坐标。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| point | common2D.Point | 是 | 指定要取反的点。 |

## offset

```TypeScript
static offset(point: common2D.Point, dx: number, dy: number): void
```

将点的坐标偏移dx, dy。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| point | common2D.Point | 是 | 指定要偏移的点。 |
| dx | number | 是 | 指示在x轴上偏移的距离（以像素为单位）。 |
| dy | number | 是 | 指示在y轴上偏移的距离（以像素为单位）。 |

