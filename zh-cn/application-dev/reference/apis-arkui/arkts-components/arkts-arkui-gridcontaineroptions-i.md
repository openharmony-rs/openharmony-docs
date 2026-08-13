# GridContainerOptions

栅格栅格布局容器配置参数对象，用于设置GridContainer组件的列数、设备宽度类型、列间距和两侧间距。 > **说明：** > > 从API version 7开始支持，从API version 9开始废弃。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** grid_col/GridColOptions and grid_row/GridRowOptions

<!--Device-unnamed-declare interface GridContainerOptions--><!--Device-unnamed-declare interface GridContainerOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## columns

```TypeScript
columns?: number | "auto"
```

当前布局总列数，number类型需为正整数。设置为number时使用固定列数布局；设置为'auto'时，系统根据设备宽度类型自动确定列数（XS为2列，SM为4列，MD为8列，LG为12列）。传入0或负数时视为未设置，系统自动确定列 数。 默认值：'auto'

**类型：** number \| "auto"

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** grid_col/GridColOptions and grid_row/GridRowOptions

<!--Device-GridContainerOptions-columns?: number | "auto"--><!--Device-GridContainerOptions-columns?: number | "auto"-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## gutter

```TypeScript
gutter?: number | string
```

栅格布局列间距，不支持百分比。number类型默认单位为vp，取值范围[0, +∞)。不设置时根据设备宽度类型自动确定：XS为12vp，SM/MD/LG为24vp。

**类型：** number \| string

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** grid_col/GridColOptions and grid_row/GridRowOptions

<!--Device-GridContainerOptions-gutter?: number | string--><!--Device-GridContainerOptions-gutter?: number | string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## margin

```TypeScript
margin?: number | string
```

栅格布局两侧间距，不支持百分比。number类型默认单位为vp，取值范围[0, +∞)。不设置时根据设备宽度类型自动确定：XS为12vp，SM为24vp，MD为32vp，LG为48vp。

**类型：** number \| string

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** grid_col/GridColOptions and grid_row/GridRowOptions

<!--Device-GridContainerOptions-margin?: number | string--><!--Device-GridContainerOptions-margin?: number | string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## sizeType

```TypeScript
sizeType?: SizeType
```

设置设备宽度类型，用于响应式布局。 默认值：SizeType.Auto

**类型：** [SizeType](arkts-arkui-sizetype-e.md)

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** grid_col/GridColOptions and grid_row/GridRowOptions

<!--Device-GridContainerOptions-sizeType?: SizeType--><!--Device-GridContainerOptions-sizeType?: SizeType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

