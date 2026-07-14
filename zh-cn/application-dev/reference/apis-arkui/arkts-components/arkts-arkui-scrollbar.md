# ScrollBar

滚动条组件ScrollBar，用于配合可滚动组件使用，如[ArcList]{@link @ohos.arkui.ArcList}、[List]{@link list}、[Grid]{@link grid}、
[Scroll]{@link scroll}、[WaterFlow]{@link water_flow}。

> **说明：**
>
> - 该组件从API version 8开始支持。后续版本如有新增内容，则采用上角标单独标记该内容的起始版本。
>
> - ScrollBar主轴方向不设置大小时，采用父组件[布局约束]{@link FrameNode:LayoutConstraint}中的maxSize作为主轴方向大小。如果ScrollBar的父组件存在可滚动组件，如
> [ArcList]{@link @ohos.arkui.ArcList}、[List]{@link list}、[Grid]{@link grid}、[Scroll]{@link scroll}、
> [WaterFlow]{@link water_flow}，建议设置ScrollBar主轴方向大小，否则ScrollBar主轴方向大小可能为无穷大。


## ScrollBar

```TypeScript
ScrollBar(value: ScrollBarOptions)
```

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | ScrollBarOptions | 是 | @returns { ScrollBarAttribute } |

## 汇总

- [ScrollBarOptions](arkts-arkui-scrollbar-scrollbaroptions-i.md)
- [ScrollBarDirection](arkts-arkui-scrollbar-scrollbardirection-e.md)
