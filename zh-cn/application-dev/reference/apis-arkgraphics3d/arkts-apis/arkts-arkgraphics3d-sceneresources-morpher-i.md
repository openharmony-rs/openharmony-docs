# Morpher

用于控制3D模型的形变，通过调整不同形变目标的权重，实现模型的动态变形效果。@interface Morpher

**起始版本：** 20

**系统能力：** SystemCapability.ArkUi.Graphics3D

## targets

```TypeScript
readonly targets: Record<string, number>
```

用于存储所有形变目标的名称和对应的权重。权重值通常在[0.0, 1.0]范围内。

**类型：** Record&lt;string, number&gt;

**起始版本：** 20

**系统能力：** SystemCapability.ArkUi.Graphics3D
