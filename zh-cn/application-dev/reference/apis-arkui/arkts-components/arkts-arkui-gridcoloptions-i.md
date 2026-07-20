# GridColOptions

设置栅格列布局组件布局选项。

`span`、`offset`、`order`属性按照`xs`、`sm`、`md`、`lg`、`xl`、`xxl`的顺序具有“继承性”，未设置值的断点将会从前一个断点取值。

API version 20之后，`span`的继承规则见[GridColColumnOption](arkts-arkui-gridcolcolumnoption-i.md)。

**起始版本：** 9

<!--Device-unnamed-declare interface GridColOptions--><!--Device-unnamed-declare interface GridColOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset?: number | GridColColumnOption
```

栅格子组件相对于原本位置偏移的列数。

取值为非负整数，默认值为0

非法值：按默认值处理。

**类型：** number \| GridColColumnOption

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-GridColOptions-offset?: number | GridColColumnOption--><!--Device-GridColOptions-offset?: number | GridColColumnOption-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## order

```TypeScript
order?: number | GridColColumnOption
```

元素的序号，根据栅格子组件的序号，从小到大对栅格子组件做排序。

取值为非负整数，默认值为0。

非法值：按默认值处理。

**说明：**

当子组件不设置order或者设置相同的order，子组件按照代码顺序展示。

当子组件部分设置order，部分不设置order时，未设置order的子组件依次排序靠前，设置了order的子组件按照数值从小到大排列。

**类型：** number \| GridColColumnOption

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-GridColOptions-order?: number | GridColColumnOption--><!--Device-GridColOptions-order?: number | GridColColumnOption-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## span

```TypeScript
span?: number | GridColColumnOption
```

栅格子组件占用栅格容器组件的列数。span为0表示该元素不参与布局计算，即不会被渲染。

取值为非负整数，默认值为1

非法值：按默认值处理。

**类型：** number \| GridColColumnOption

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-GridColOptions-span?: number | GridColColumnOption--><!--Device-GridColOptions-span?: number | GridColColumnOption-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

