# CounterV2Options

CounterV2Options定义CounterV2类型及样式。选择不同的CounterV2类型，需要选择对应的CounterV2样式。若样式参数与类型不匹配，将使用该类型对应的默认样式。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { CounterV2Component, CounterV2Options, CounterV2DateData, CounterV2Type } from '@kit.ArkUI';
```

## dateOptions

```TypeScript
dateOptions?: CounterV2DateStyleOptions
```

日期内联型CounterV2的样式。默认值：undefined，显示0001/01/01的日期内联型CounterV2。当需要自定义日期内联型CounterV2的初始日期、日期变化回调等属性时传入此参数；当需要显示默认日期0001/01/01且不需要自定义配置时可以不传入，使用默认样式。值为undefined时，按默认值处理。

**类型：** [CounterV2DateStyleOptions](arkts-arkui-arkui-advanced-counterv2-counterv2datestyleoptions-c.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction?: Direction
```

布局方向。默认值：Direction.Auto值为undefined时，按默认值处理。

**类型：** Direction

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## inlineOptions

```TypeScript
inlineOptions?: CounterV2InlineStyleOptions
```

数值内联型CounterV2的样式。默认值：undefined，显示数值为0的数值内联型CounterV2。当需要自定义数值内联型CounterV2的初始值、范围、步长、文本宽度、变化回调等属性时传入此参数；当计数器初始值为0且不需要自定义配置时可以不传入，使用默认样式。值为undefined时，按默认值处理。

**类型：** [CounterV2InlineStyleOptions](arkts-arkui-arkui-advanced-counterv2-counterv2inlinestyleoptions-c.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## numberOptions

```TypeScript
numberOptions?: CounterV2NumberStyleOptions
```

列表型和紧凑型CounterV2的样式。默认值：undefined，显示数值为0的列表型或紧凑型CounterV2。当需要自定义列表型或紧凑型CounterV2的标签、初始值、范围、步长等属性时传入此参数；当计数器初始值为0且不需要自定义配置时可以不传入，使用默认样式。值为undefined时，按默认值处理。

**类型：** [CounterV2NumberStyleOptions](arkts-arkui-arkui-advanced-counterv2-counterv2numberstyleoptions-c.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: CounterV2Type
```

指定当前CounterV2的类型。需配合对应的样式参数使用，具体对应关系见下表。

**类型：** [CounterV2Type](arkts-arkui-arkui-advanced-counterv2-counterv2type-e.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
