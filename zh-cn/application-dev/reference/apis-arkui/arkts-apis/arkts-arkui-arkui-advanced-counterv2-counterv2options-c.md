# CounterV2Options

CounterV2Options定义CounterV2类型及样式。

**起始版本：** 26.0.0

<!--Device-unnamed-declare class CounterV2Options--><!--Device-unnamed-declare class CounterV2Options-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { CounterV2Component, CounterV2Options, CounterV2Type, CounterV2DateData } from '@kit.ArkUI';
```

## dateOptions

```TypeScript
dateOptions?: CounterV2DateStyleOptions
```

日期内联型CounterV2的样式。

默认值：显示0001/01/01的日期内联型CounterV2。

值为undefined时，按默认值处理。

**类型：** CounterV2DateStyleOptions

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CounterV2Options-dateOptions?: CounterV2DateStyleOptions--><!--Device-CounterV2Options-dateOptions?: CounterV2DateStyleOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction?: Direction
```

布局方向。

默认值：Direction.Auto

值为undefined时，按默认值处理。

**类型：** Direction

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CounterV2Options-direction?: Direction--><!--Device-CounterV2Options-direction?: Direction-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## inlineOptions

```TypeScript
inlineOptions?: CounterV2InlineStyleOptions
```

普通数字内联调节型CounterV2的样式。

默认值：显示计数器为0的普通数字内联调节型CounterV2。

值为undefined时，按默认值处理。

**类型：** CounterV2InlineStyleOptions

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CounterV2Options-inlineOptions?: CounterV2InlineStyleOptions--><!--Device-CounterV2Options-inlineOptions?: CounterV2InlineStyleOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## numberOptions

```TypeScript
numberOptions?: CounterV2NumberStyleOptions
```

列表型和紧凑型CounterV2的样式。

默认值：显示计数器为0的列表型或紧凑型CounterV2。

值为undefined时，按默认值处理。

**类型：** CounterV2NumberStyleOptions

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CounterV2Options-numberOptions?: CounterV2NumberStyleOptions--><!--Device-CounterV2Options-numberOptions?: CounterV2NumberStyleOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: CounterV2Type
```

指定当前CounterV2的类型。

**类型：** CounterV2Type

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-CounterV2Options-type: CounterV2Type--><!--Device-CounterV2Options-type: CounterV2Type-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

