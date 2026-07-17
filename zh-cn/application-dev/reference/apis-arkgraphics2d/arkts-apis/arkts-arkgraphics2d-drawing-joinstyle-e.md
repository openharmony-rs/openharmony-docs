# JoinStyle

定义线条转角样式的枚举，即画笔在绘制折线段时，在折线转角处的样式。

**起始版本：** 12

<!--Device-drawing-enum JoinStyle--><!--Device-drawing-enum JoinStyle-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## MITER_JOIN

```TypeScript
MITER_JOIN = 0
```

转角类型为尖角，如果折线角度比较小，则尖角会很长，需要使用限制值（miter limit）进行限制。

**起始版本：** 12

<!--Device-JoinStyle-MITER_JOIN = 0--><!--Device-JoinStyle-MITER_JOIN = 0-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## ROUND_JOIN

```TypeScript
ROUND_JOIN = 1
```

转角类型为圆头。

**起始版本：** 12

<!--Device-JoinStyle-ROUND_JOIN = 1--><!--Device-JoinStyle-ROUND_JOIN = 1-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## BEVEL_JOIN

```TypeScript
BEVEL_JOIN = 2
```

转角类型为平头。

**起始版本：** 12

<!--Device-JoinStyle-BEVEL_JOIN = 2--><!--Device-JoinStyle-BEVEL_JOIN = 2-End-->

**系统能力：** SystemCapability.Graphics.Drawing

