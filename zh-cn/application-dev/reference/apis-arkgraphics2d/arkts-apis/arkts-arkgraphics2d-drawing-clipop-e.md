# ClipOp

画布裁剪方式的枚举。
> **说明：**  
>  
> 示意图展示了以INTERSECT方式裁剪一个矩形后，使用不同枚举值继续裁剪一个圆形的结果，绿色区域为最终的裁剪区域。

**起始版本：** 12

<!--Device-drawing-enum ClipOp--><!--Device-drawing-enum ClipOp-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## DIFFERENCE

```TypeScript
DIFFERENCE = 0
```

将指定区域裁剪（取差集）。

**起始版本：** 12

<!--Device-ClipOp-DIFFERENCE = 0--><!--Device-ClipOp-DIFFERENCE = 0-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## INTERSECT

```TypeScript
INTERSECT = 1
```

将指定区域保留（取交集）。

**起始版本：** 12

<!--Device-ClipOp-INTERSECT = 1--><!--Device-ClipOp-INTERSECT = 1-End-->

**系统能力：** SystemCapability.Graphics.Drawing

