# SrcRectConstraint

源矩形区域约束类型枚举，用于在画布绘制图像时指定是否将采样范围限制在源矩形区域内。

**起始版本：** 12

<!--Device-drawing-enum SrcRectConstraint--><!--Device-drawing-enum SrcRectConstraint-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## STRICT

```TypeScript
STRICT = 0
```

严格限制采样范围在源矩形区域内，速度较慢。

**起始版本：** 12

<!--Device-SrcRectConstraint-STRICT = 0--><!--Device-SrcRectConstraint-STRICT = 0-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## FAST

```TypeScript
FAST = 1
```

允许采样范围超出源矩形范围，速度较快。

**起始版本：** 12

<!--Device-SrcRectConstraint-FAST = 1--><!--Device-SrcRectConstraint-FAST = 1-End-->

**系统能力：** SystemCapability.Graphics.Drawing

