# SamplerFilter

采样器过滤模式枚举，定义纹理采样时的插值方法，用于控制纹理在缩放或变形时如何计算最终像素的颜色值。@enum { number }

**起始版本：** 20

**系统能力：** SystemCapability.ArkUi.Graphics3D

## NEAREST

```TypeScript
NEAREST = 0
```

使用最近邻插值进行采样，速度快但边缘可能锯齿明显。

**起始版本：** 20

**系统能力：** SystemCapability.ArkUi.Graphics3D

## LINEAR

```TypeScript
LINEAR = 1
```

使用线性插值进行采样，效果更平滑但性能略低。

**起始版本：** 20

**系统能力：** SystemCapability.ArkUi.Graphics3D
