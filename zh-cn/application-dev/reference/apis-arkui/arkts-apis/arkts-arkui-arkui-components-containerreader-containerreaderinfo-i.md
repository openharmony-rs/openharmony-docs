# ContainerReaderInfo

定义ContainerReader组件的配置选项，用于指定容器尺寸读取和断点值获取的参数，不能通过此参数改变组件尺寸和断点值。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

<!--Device-unnamed-export interface ContainerReaderInfo--><!--Device-unnamed-export interface ContainerReaderInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## heightBreakpoint

```TypeScript
heightBreakpoint?: HeightBreakpoint
```

容器的高度断点，为获取到的当前ContainerReader组件在不同高宽比阈值下对应的高度断点枚举值。\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_**说明：**\_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_该参数支持\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_双向绑定变量。绑定后组件高度断点值变化时，heightBreakpoint绑定的变量值会自动更新。

**类型：** HeightBreakpoint

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-ContainerReaderInfo-heightBreakpoint?: HeightBreakpoint--><!--Device-ContainerReaderInfo-heightBreakpoint?: HeightBreakpoint-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size: Size
```

获取到的当前ContainerReader组件的尺寸，用于布局分析和断点计算。\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_**说明：**\_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_该参数支持\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_双向绑定变量。绑定后组件尺寸值变化时，size绑定的变量值会自动更新。

**类型：** Size

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-ContainerReaderInfo-size: Size--><!--Device-ContainerReaderInfo-size: Size-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## widthBreakpoint

```TypeScript
widthBreakpoint?: WidthBreakpoint
```

容器的宽度断点，为获取到的当前ContainerReader组件的宽度断点枚举值。\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_**说明：**\_\_\_HTML\_TAG\_DESC\_USD\_2\_\_\_该参数支持\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_双向绑定变量。绑定后组件宽度断点值变化时，widthBreakpoint绑定的变量值会自动更新。

**类型：** WidthBreakpoint

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-ContainerReaderInfo-widthBreakpoint?: WidthBreakpoint--><!--Device-ContainerReaderInfo-widthBreakpoint?: WidthBreakpoint-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

