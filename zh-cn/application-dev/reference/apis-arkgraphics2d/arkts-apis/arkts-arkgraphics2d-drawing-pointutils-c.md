# PointUtils

This class offers a comprehensive set of operations for handling common2D Point objects.

**起始版本：** 26.0.0

<!--Device-drawing-class PointUtils--><!--Device-drawing-class PointUtils-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## 导入模块

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';
```

<a id="negate"></a>
## negate

```TypeScript
static negate(point: common2D.Point): void
```

取反点的坐标。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PointUtils-static negate(point: common2D.Point): void--><!--Device-PointUtils-static negate(point: common2D.Point): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| point | common2D.Point | 是 | 指定要取反的点。 |

<a id="offset"></a>
## offset

```TypeScript
static offset(point: common2D.Point, dx: number, dy: number): void
```

将点的坐标偏移dx, dy。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PointUtils-static offset(point: common2D.Point, dx: double, dy: double): void--><!--Device-PointUtils-static offset(point: common2D.Point, dx: double, dy: double): void-End-->

**系统能力：** SystemCapability.Graphics.Drawing

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| point | common2D.Point | 是 | 指定要偏移的点。 |
| dx | number | 是 | 指示在x轴上偏移的距离（以像素为单位）。 |
| dy | number | 是 | 指示在y轴上偏移的距离（以像素为单位）。 |

