# BreakpointOptions

定义断点配置选项，用于指定容器尺寸分析的阈值参数。

**起始版本：** 26.0.0

<!--Device-unnamed-export interface BreakpointOptions--><!--Device-unnamed-export interface BreakpointOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { BreakpointOptions, ContainerReader, ContainerReaderAttribute } from '@kit.ArkUI';
```

## height

```TypeScript
height?: Array<number>
```

高度断点值数组，高度断点值是组件高度与宽度的比值。无单位。数组必须为单调递增数组。<br/>默认值：[0.8, 1.2]，与窗口高度断点默认值一致。<br/>**说明：**<br/>最多支持3个断点，即数组最大长度为2。

**类型：** Array&lt;number&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-BreakpointOptions-height?: Array<double>--><!--Device-BreakpointOptions-height?: Array<double>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## width

```TypeScript
width?: Array<number>
```

宽度断点值数组。数组必须为单调递增数组。<br/>默认值：[320, 600, 840, 1440]，单位vp，与窗口宽度断点默认值一致。<br/>**说明：**<br/>最多可支持5个断点，即数组最大长度为4。

**类型：** Array&lt;number&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-BreakpointOptions-width?: Array<double>--><!--Device-BreakpointOptions-width?: Array<double>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

