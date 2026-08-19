# RegionOp

两个区域合并时的操作的枚举。常用于图形编辑、裁剪区域计算等需要组合多个区域的场景。 > **说明：** > > 示意图展示了一个以红色区域为基础，使用不同枚举值与另一个蓝色区域合并后获得的结果，其中绿色区域为最终得到的区域。

**起始版本：** 23

<!--Device-drawing-enum RegionOp--><!--Device-drawing-enum RegionOp-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## DIFFERENCE

```TypeScript
DIFFERENCE = 0
```

两个区域的相减操作，从第一个区域中减去第二个区域。适用于需要裁剪掉特定区域的场景。

**起始版本：** 23

<!--Device-RegionOp-DIFFERENCE = 0--><!--Device-RegionOp-DIFFERENCE = 0-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## INTERSECT

```TypeScript
INTERSECT = 1
```

两个区域的相交操作，保留两个区域重叠的部分。适用于需要获取公共区域的场景。

**起始版本：** 23

<!--Device-RegionOp-INTERSECT = 1--><!--Device-RegionOp-INTERSECT = 1-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## UNION

```TypeScript
UNION = 2
```

两个区域的联合操作，合并两个区域的所有部分。适用于需要合并区域的场景。

**起始版本：** 23

<!--Device-RegionOp-UNION = 2--><!--Device-RegionOp-UNION = 2-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## XOR

```TypeScript
XOR = 3
```

两个区域的异或操作，保留两个区域不重叠的部分。适用于需要获取非重叠区域的场景。

**起始版本：** 23

<!--Device-RegionOp-XOR = 3--><!--Device-RegionOp-XOR = 3-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## REVERSE_DIFFERENCE

```TypeScript
REVERSE_DIFFERENCE = 4
```

两个区域的反向相减操作，从第二个区域中减去第一个区域。适用于需要反向裁剪的场景。

**起始版本：** 23

<!--Device-RegionOp-REVERSE_DIFFERENCE = 4--><!--Device-RegionOp-REVERSE_DIFFERENCE = 4-End-->

**系统能力：** SystemCapability.Graphics.Drawing

## REPLACE

```TypeScript
REPLACE = 5
```

两个区域替换操作，用第二个区域完全替换第一个区域。适用于需要完全覆盖的场景。

**起始版本：** 23

<!--Device-RegionOp-REPLACE = 5--><!--Device-RegionOp-REPLACE = 5-End-->

**系统能力：** SystemCapability.Graphics.Drawing

