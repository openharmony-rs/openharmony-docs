# CounterV2Component

CounterV2组件用于精确调节数值，包含列表型、紧凑型、数值内联型和日期内联型四种类型，适用于购物车数量调节、日期选择等场景。该组件基于[状态管理（V2）](../../../ui/state-management/arkts-state-management-overview.md#状态管理v2)实现，相较于 [状态管理（V1）](../../../ui/state-management/arkts-state-management-overview.md#状态管理v1)，状态管理（V2）增强了对数据对象的深度观察与管理能力，不再局限于组 件层级。借助状态管理（V2），开发者可以通过该组件更灵活地控制CounterV2的数据和状态，实现更高效的用户界面刷新。

> **说明：**
> 
> - 如果CounterV2设置通用属性和通用事件，编译工具链会
> 额外生成节点__Common__，并将通用属性或通用事件挂载在__Common__上，而不是直接应用到CounterV2本身。这可能导致开发者设置的通用属性或通用事件不生效或不符合预期，因此，不建议为CounterV2设置通用属性
> 和通用事件。
> 
> - 该组件接口仅可在Stage模型下使用。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { CounterV2Component, CounterV2Options, CounterV2DateData, CounterV2Type } from '@kit.ArkUI';
```

## options

```TypeScript
options: CounterV2Options
```

定义CounterV2组件的类型及样式。

**类型：** [CounterV2Options](arkts-arkui-arkui-advanced-counterv2-counterv2options-c.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
