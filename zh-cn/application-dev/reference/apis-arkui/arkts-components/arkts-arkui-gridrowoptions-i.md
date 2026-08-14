# GridRowOptions

设置栅格行布局容器的布局选项。

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

<!--Device-unnamed-declare interface GridRowOptions--><!--Device-unnamed-declare interface GridRowOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## breakpoints

```TypeScript
breakpoints?: BreakPoints
```

设置断点位置的单调递增数组，以及断点切换时的参照对象（基于应用窗口或容器尺寸）。 默认值： { value: ["320vp", "600vp", "840vp"], reference: BreakpointsReference.WindowSize } 非法值：按默认值处理。 单位：vp

**类型：** [BreakPoints](arkts-arkui-breakpoints-i.md)

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-GridRowOptions-breakpoints?: BreakPoints--><!--Device-GridRowOptions-breakpoints?: BreakPoints-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## columns

```TypeScript
columns?: number | GridRowColumnOption
```

设置布局列数。 取值为大于0的整数。 - API version 20之前：默认值为12。 - API version 20及之后：默认值为{ xs: 2, sm: 4, md: 8, lg: 12, xl: 12, xxl: 12 } 非法值：按默认值处理。

**类型：** number \| [GridRowColumnOption](arkts-arkui-gridrowcolumnoption-i.md)

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-GridRowOptions-columns?: number | GridRowColumnOption--><!--Device-GridRowOptions-columns?: number | GridRowColumnOption-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction?: GridRowDirection
```

栅格布局排列方向。支持Row（行方向排列，适用于常规LTR布局）和RowReverse（逆序行方向排列，适用于RTL布局或需要反向排列的场景）。 默认值：GridRowDirection.Row 非法值：按默认值处理。

**类型：** [GridRowDirection](arkts-arkui-gridrowdirection-e.md)

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-GridRowOptions-direction?: GridRowDirection--><!--Device-GridRowOptions-direction?: GridRowDirection-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## gutter

```TypeScript
gutter?: Length | GutterOption
```

栅格布局间距。 默认值：0vp 非法值：按默认值处理。 单位：vp

**类型：** Length \| [GutterOption](arkts-arkui-gutteroption-i.md)

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-GridRowOptions-gutter?: Length | GutterOption--><!--Device-GridRowOptions-gutter?: Length | GutterOption-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

