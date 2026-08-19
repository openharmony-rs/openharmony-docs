# ContainerReaderInfo

定义ContainerReader组件的配置选项，用于指定容器尺寸读取和断点值获取的参数，不能通过此参数改变组件尺寸和断点值。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export declare interface ContainerReaderInfo--><!--Device-unnamed-export declare interface ContainerReaderInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## heightBreakpoint

```TypeScript
heightBreakpoint?: Bindable<HeightBreakpoint>
```

容器的高度断点，为获取到的当前ContainerReader组件在不同高宽比阈值下对应的高度断点枚举值。 > **说明：** > > 该参数支持[!!](../../../ui/state-management/arkts-new-binding.md#系统组件参数双向绑定)双向绑定变量。绑定后组件高度断点值变化时， > heightBreakpoint绑定的变量值会自动更新。

**类型：** [Bindable](arkts-na-common-bindable-i.md)&lt;HeightBreakpoint&gt;

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ContainerReaderInfo-heightBreakpoint?: Bindable<HeightBreakpoint>--><!--Device-ContainerReaderInfo-heightBreakpoint?: Bindable<HeightBreakpoint>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size: Bindable<Size>
```

获取到的当前ContainerReader组件的尺寸，用于布局分析和断点计算。 > **说明：** > > 该参数支持[!!](../../../ui/state-management/arkts-new-binding.md#系统组件参数双向绑定)双向绑定变量。绑定后组件尺寸值变化时，size绑定的变量值会自动更新。

**类型：** [Bindable](arkts-na-common-bindable-i.md)&lt;[Size](../../apis-arkui/arkts-apis/arkts-arkui-graphics-size-i.md)&gt;

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ContainerReaderInfo-size: Bindable<Size>--><!--Device-ContainerReaderInfo-size: Bindable<Size>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## widthBreakpoint

```TypeScript
widthBreakpoint?: Bindable<WidthBreakpoint>
```

容器的宽度断点，为获取到的当前ContainerReader组件的宽度断点枚举值。 > **说明：** > > 该参数支持[!!](../../../ui/state-management/arkts-new-binding.md#系统组件参数双向绑定)双向绑定变量。绑定后组件宽度断点值变化时， > widthBreakpoint绑定的变量值会自动更新。

**类型：** [Bindable](arkts-na-common-bindable-i.md)&lt;WidthBreakpoint&gt;

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ContainerReaderInfo-widthBreakpoint?: Bindable<WidthBreakpoint>--><!--Device-ContainerReaderInfo-widthBreakpoint?: Bindable<WidthBreakpoint>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

