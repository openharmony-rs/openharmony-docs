# LineMetrics

描述文本布局中单行文字的度量信息。

**起始版本：** 23

<!--Device-text-interface LineMetrics--><!--Device-text-interface LineMetrics-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## 导入模块

```TypeScript
import { text } from '@kit.ArkGraphics2D';
```

## ascent

```TypeScript
ascent: double
```

文字上升高度，即从基线到字符顶部的距离，单位为物理像素px。

**类型：** double

**起始版本：** 23

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-LineMetrics-ascent: double--><!--Device-LineMetrics-ascent: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## baseline

```TypeScript
baseline: double
```

该行基线相对于段落顶部的 Y 坐标位置，单位为物理像素px。

**类型：** double

**起始版本：** 23

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-LineMetrics-baseline: double--><!--Device-LineMetrics-baseline: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## descent

```TypeScript
descent: double
```

文字下降高度，即从基线到字符底部的距离，单位为物理像素px。

**类型：** double

**起始版本：** 23

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-LineMetrics-descent: double--><!--Device-LineMetrics-descent: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## endIndex

```TypeScript
endIndex: int
```

文本缓冲区中该行结束的索引位置。

**类型：** int

**起始版本：** 23

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-LineMetrics-endIndex: int--><!--Device-LineMetrics-endIndex: int-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## height

```TypeScript
height: double
```

当前行的高度，单位为物理像素px，计算方式为 `Math.round(ascent + descent)`

**类型：** double

**起始版本：** 23

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-LineMetrics-height: double--><!--Device-LineMetrics-height: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## left

```TypeScript
left: double
```

行的左边缘位置，单位为物理像素px。右边缘可通过 `left+width` 计算得出。

**类型：** double

**起始版本：** 23

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-LineMetrics-left: double--><!--Device-LineMetrics-left: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## lineNumber

```TypeScript
lineNumber: int
```

行号，从0开始计数。

**类型：** int

**起始版本：** 23

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-LineMetrics-lineNumber: int--><!--Device-LineMetrics-lineNumber: int-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## runMetrics

```TypeScript
runMetrics: Map<int, RunMetrics>
```

文本索引范围与关联的字体度量信息之间的映射。

**类型：** Map&lt;int, [RunMetrics](arkts-arkgraphics2d-text-runmetrics-i.md)&gt;

**起始版本：** 23

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-LineMetrics-runMetrics: Map<int, RunMetrics>--><!--Device-LineMetrics-runMetrics: Map<int, RunMetrics>-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## startIndex

```TypeScript
startIndex: int
```

文本缓冲区中该行开始的索引位置。

**类型：** int

**起始版本：** 23

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-LineMetrics-startIndex: int--><!--Device-LineMetrics-startIndex: int-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## topHeight

```TypeScript
topHeight: double
```

从顶部到当前行的高度，单位为物理像素px。

**类型：** double

**起始版本：** 23

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-LineMetrics-topHeight: double--><!--Device-LineMetrics-topHeight: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## width

```TypeScript
width: double
```

行的宽度，单位为物理像素px。

**类型：** double

**起始版本：** 23

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-LineMetrics-width: double--><!--Device-LineMetrics-width: double-End-->

**系统能力：** SystemCapability.Graphics.Drawing

