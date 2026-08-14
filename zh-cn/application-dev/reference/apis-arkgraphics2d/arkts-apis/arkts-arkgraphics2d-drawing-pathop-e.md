# PathOp

路径操作类型枚举，可用于合并或裁剪路径等功能。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-drawing-enum PathOp--><!--Device-drawing-enum PathOp-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## DIFFERENCE

```TypeScript
DIFFERENCE = 0
```

差集操作，保留第一条路径中不与第二条路径重叠的区域。适用于需要从路径中减去某些区域的场景。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-PathOp-DIFFERENCE = 0--><!--Device-PathOp-DIFFERENCE = 0-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## INTERSECT

```TypeScript
INTERSECT = 1
```

交集操作，保留两条路径重叠的区域。适用于需要获取路径交集部分的场景。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-PathOp-INTERSECT = 1--><!--Device-PathOp-INTERSECT = 1-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## UNION

```TypeScript
UNION = 2
```

并集操作，合并两条路径的所有区域。适用于需要合并多个路径的场景。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-PathOp-UNION = 2--><!--Device-PathOp-UNION = 2-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## XOR

```TypeScript
XOR = 3
```

异或操作，保留两条路径不重叠的区域。适用于需要获取路径非重叠部分的场景。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-PathOp-XOR = 3--><!--Device-PathOp-XOR = 3-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## REVERSE_DIFFERENCE

```TypeScript
REVERSE_DIFFERENCE = 4
```

反向差集操作，保留第二条路径中不与第一条路径重叠的区域。适用于需要反向减去路径的场景。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-PathOp-REVERSE_DIFFERENCE = 4--><!--Device-PathOp-REVERSE_DIFFERENCE = 4-End-->

**系统能力：** SystemCapability.Graphics.Drawing

