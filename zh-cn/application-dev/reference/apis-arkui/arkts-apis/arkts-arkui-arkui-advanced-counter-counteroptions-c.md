# CounterOptions

CounterOptions定义Counter类型及样式。

**起始版本：** 11

<!--Device-unnamed-declare class CounterOptions--><!--Device-unnamed-declare class CounterOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { CounterType, DateData, CounterComponent, CounterOptions } from '@kit.ArkUI';
```

## dateOptions

```TypeScript
dateOptions?: DateStyleOptions
```

日期型内联型Counter的样式。

默认值：显示0001/01/01的日期型内联型Counter。

值为undefined时，按默认值处理。

**类型：** DateStyleOptions

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CounterOptions-dateOptions?: DateStyleOptions--><!--Device-CounterOptions-dateOptions?: DateStyleOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction?: Direction
```

布局方向。

默认值：Direction.Auto

值为undefined时，按默认值处理。

**类型：** Direction

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CounterOptions-direction?: Direction--><!--Device-CounterOptions-direction?: Direction-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## inlineOptions

```TypeScript
inlineOptions?: InlineStyleOptions
```

普通数字内联调节型Counter的样式。

默认值：显示计数器为0的普通数字内联调节型Counter。

值为undefined时，按默认值处理。

**类型：** InlineStyleOptions

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CounterOptions-inlineOptions?: InlineStyleOptions--><!--Device-CounterOptions-inlineOptions?: InlineStyleOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## numberOptions

```TypeScript
numberOptions?: NumberStyleOptions
```

列表型和紧凑型Counter的样式。

默认值：显示计数器为0的列表型或紧凑型Counter。

值为undefined时，按默认值处理。

**类型：** NumberStyleOptions

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CounterOptions-numberOptions?: NumberStyleOptions--><!--Device-CounterOptions-numberOptions?: NumberStyleOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: CounterType
```

指定当前Counter的类型。

**类型：** CounterType

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-CounterOptions-type: CounterType--><!--Device-CounterOptions-type: CounterType-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

