# ContainerReaderInfo

定义ContainerReader组件的配置选项，用于指定容器尺寸读取和断点值获取的参数，不能通过此参数改变组件尺寸和断点值。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { ContainerReader, ContainerReaderAttribute, BreakpointOptions } from '@kit.ArkUI';
```

## heightBreakpoint

```TypeScript
heightBreakpoint?: HeightBreakpoint
```

容器的高度断点，为获取到的当前ContainerReader组件在不同高宽比阈值下对应的高度断点枚举值。  
**说明：**该参数支持[!!](../../../ui/state-management/arkts-new-binding.md)双向绑定变量。绑定后组件高度断点值变化时，heightBreakpoint绑定的变量值会自动更新。

**类型：** [HeightBreakpoint](arkts-arkui-heightbreakpoint-e.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size: Size
```

获取到的当前ContainerReader组件的尺寸，用于布局分析和断点计算。  
**说明：**该参数支持[!!](../../../ui/state-management/arkts-new-binding.md)双向绑定变量。绑定后组件尺寸值变化时，size绑定的变量值会自动更新。

**类型：** Size

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## widthBreakpoint

```TypeScript
widthBreakpoint?: WidthBreakpoint
```

容器的宽度断点，为获取到的当前ContainerReader组件的宽度断点枚举值。  
**说明：**该参数支持[!!](../../../ui/state-management/arkts-new-binding.md)双向绑定变量。绑定后组件宽度断点值变化时，widthBreakpoint绑定的变量值会自动更新。

**类型：** [WidthBreakpoint](arkts-arkui-widthbreakpoint-e.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
