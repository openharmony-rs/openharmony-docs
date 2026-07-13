# BreakPoints

设置栅格容器组件的断点。更多断点的说明参考[栅格容器断点](../../../../ui/arkts-layout-development-grid-layout.md#栅格容器断点)。

<!--code_no_check-->

**起始版本：** 9

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## reference

```TypeScript
reference?: BreakpointsReference
```

断点切换参照物。

默认值：BreakpointsReference.WindowSize

非法值：按默认值处理。

**类型：** BreakpointsReference

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value?: Array<string>
```

设置断点位置的单调递增数组。

默认值：["320vp", "600vp", "840vp"]

非法值：按默认值处理。

单位：vp

**类型：** Array<string>

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

