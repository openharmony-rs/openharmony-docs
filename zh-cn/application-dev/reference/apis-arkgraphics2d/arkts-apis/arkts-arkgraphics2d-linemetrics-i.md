# LineMetrics

描述文本布局中单行文字的度量信息。

**起始版本：** 12

**系统能力：** SystemCapability.Graphics.Drawing

## ascent

```TypeScript
ascent: number
```

文字上升高度，即从基线到字符顶部的距离，单位为物理像素px。

**类型：** number

**起始版本：** 12

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphics.Drawing

## baseline

```TypeScript
baseline: number
```

该行基线相对于段落顶部的 Y 坐标位置，单位为物理像素px。

**类型：** number

**起始版本：** 12

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphics.Drawing

## descent

```TypeScript
descent: number
```

文字下降高度，即从基线到字符底部的距离，单位为物理像素px。

**类型：** number

**起始版本：** 12

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphics.Drawing

## endIndex

```TypeScript
endIndex: number
```

文本缓冲区中该行结束的索引位置。

**类型：** number

**起始版本：** 12

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphics.Drawing

## height

```TypeScript
height: number
```

当前行的高度，单位为物理像素px，计算方式为 `Math.round(ascent + descent)`

**类型：** number

**起始版本：** 12

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphics.Drawing

## left

```TypeScript
left: number
```

行的左边缘位置，单位为物理像素px。右边缘可通过 `left+width` 计算得出。

**类型：** number

**起始版本：** 12

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphics.Drawing

## lineNumber

```TypeScript
lineNumber: number
```

行号，从0开始计数。

**类型：** number

**起始版本：** 12

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphics.Drawing

## runMetrics

```TypeScript
runMetrics: Map<number, RunMetrics>
```

文本索引范围与关联的字体度量信息之间的映射。

**类型：** Map<number, RunMetrics>

**起始版本：** 12

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphics.Drawing

## startIndex

```TypeScript
startIndex: number
```

文本缓冲区中该行开始的索引位置。

**类型：** number

**起始版本：** 12

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphics.Drawing

## topHeight

```TypeScript
topHeight: number
```

从顶部到当前行的高度，单位为物理像素px。

**类型：** number

**起始版本：** 12

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphics.Drawing

## width

```TypeScript
width: number
```

行的宽度，单位为物理像素px。

**类型：** number

**起始版本：** 12

**元服务API：** 从API版本22开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Graphics.Drawing

