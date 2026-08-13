# WindowSizeLayoutBreakpointInfo

定义窗口大小断点信息。 这个接口定义了当前窗口长宽的断点信息，基于配置好的断点阈值。

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

<!--Device-uiObserver-export interface WindowSizeLayoutBreakpointInfo--><!--Device-uiObserver-export interface WindowSizeLayoutBreakpointInfo-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## heightBreakpoint

```TypeScript
readonly heightBreakpoint: HeightBreakpoint
```

当前窗口的高度断点分类。该值根据已配置的高度断点阈值和宽高比，指示窗口当前所处的高度类别。

**类型：** HeightBreakpoint

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowSizeLayoutBreakpointInfo-readonly heightBreakpoint: HeightBreakpoint--><!--Device-WindowSizeLayoutBreakpointInfo-readonly heightBreakpoint: HeightBreakpoint-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## widthBreakpoint

```TypeScript
readonly widthBreakpoint: WidthBreakpoint
```

当前窗口的宽度断点分类。该值根据已配置的宽度断点阈值，指示窗口当前处于哪个宽度类别。

**类型：** WidthBreakpoint

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-WindowSizeLayoutBreakpointInfo-readonly widthBreakpoint: WidthBreakpoint--><!--Device-WindowSizeLayoutBreakpointInfo-readonly widthBreakpoint: WidthBreakpoint-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

