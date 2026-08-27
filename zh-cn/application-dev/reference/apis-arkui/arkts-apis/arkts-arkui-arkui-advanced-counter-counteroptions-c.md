# CounterOptions

CounterOptions定义了Counter类型及样式。选择不同的Counter类型时，需选择对应的Counter样式。若样式参数与类型不匹配，将使用该类型对应的默认样式。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { CounterComponent, CounterOptions, CounterType, DateData } from '@kit.ArkUI';
```

## dateOptions

```TypeScript
dateOptions?: DateStyleOptions
```

日期内联型Counter的样式。需配合type为CounterType.INLINE_DATE使用。默认值：显示0001/01/01的日期内联型Counter。值为undefined时，按默认值处理。

**类型：** [DateStyleOptions](arkts-arkui-arkui-advanced-counter-datestyleoptions-c.md)

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction?: Direction
```

布局方向。当需要适配从右到左的语言（如阿拉伯语）或实现镜像布局时传入此参数。Direction.Auto：自动跟随系统语言方向（默认）；Direction.Ltr：从左到右布局，适用于大多数语言；Direction.Rtl：从右到 左布局，适用于阿拉伯语等RTL语言。默认值：Direction.Auto值为undefined时，按默认值处理。

**类型：** Direction

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## inlineOptions

```TypeScript
inlineOptions?: InlineStyleOptions
```

数值内联型Counter的样式。需配合type为CounterType.INLINE使用。默认值：显示计数器为0的数值内联型Counter。值为undefined时，按默认值处理。

**类型：** [InlineStyleOptions](arkts-arkui-arkui-advanced-counter-inlinestyleoptions-c.md)

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## numberOptions

```TypeScript
numberOptions?: NumberStyleOptions
```

列表型和紧凑型Counter的样式。需配合type为CounterType.LIST或CounterType.COMPACT使用。默认值：显示计数器为0的列表型或紧凑型Counter。值为undefined时，按默认值处理。

**类型：** [NumberStyleOptions](arkts-arkui-arkui-advanced-counter-numberstyleoptions-c.md)

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: CounterType
```

指定当前Counter的类型。需配合对应的样式参数使用，具体对应关系参见Counter类型与样式对照表。

**类型：** [CounterType](arkts-arkui-arkui-advanced-counter-countertype-e.md)

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
