# BarMode

TabBar布局模式枚举。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare enum BarMode--><!--Device-unnamed-export declare enum BarMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Scrollable

```TypeScript
Scrollable = 0
```

每一个TabBar均使用实际布局宽度，超过总长度（横向Tabs的barWidth，纵向Tabs的 barHeight）后可滑动。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BarMode-Scrollable = 0--><!--Device-BarMode-Scrollable = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## Fixed

```TypeScript
Fixed = 1
```

所有TabBar平均分配barWidth宽度（纵向时平均分配barHeight高度）。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-BarMode-Fixed = 1--><!--Device-BarMode-Fixed = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

