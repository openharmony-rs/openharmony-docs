# NumberStyleOptions

NumberStyleOptions定义了列表型和紧凑型Counter的属性和事件。

继承于[InlineStyleOptions](arkts-arkui-arkui-advanced-counter-inlinestyleoptions-c.md)。

**继承/实现关系：** NumberStyleOptions extends [InlineStyleOptions](arkts-arkui-arkui-advanced-counter-inlinestyleoptions-c.md)

**起始版本：** 11

<!--Device-unnamed-declare class NumberStyleOptions extends InlineStyleOptions--><!--Device-unnamed-declare class NumberStyleOptions extends InlineStyleOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { CounterType, DateData, CounterComponent, CounterOptions } from '@kit.ArkUI';
```

## label

```TypeScript
label?: ResourceStr
```

设置Counter的说明文本。

默认值：' '

值为undefined时，按默认值处理。

**类型：** ResourceStr

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NumberStyleOptions-label?: ResourceStr--><!--Device-NumberStyleOptions-label?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onBlurDecrease

```TypeScript
onBlurDecrease?: () => void
```

当前Counter组件的减小按钮失去焦点时触发的回调。

默认值：不触发减少按钮失去焦点时的回调。

值为undefined时，按默认值处理。

**类型：** () => void

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NumberStyleOptions-onBlurDecrease?: () => void--><!--Device-NumberStyleOptions-onBlurDecrease?: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onBlurIncrease

```TypeScript
onBlurIncrease?: () => void
```

当前Counter组件的增加按钮失去焦点时触发的回调。

默认值：不触发增加按钮失去焦点时的回调。

值为undefined时，按默认值处理。

**类型：** () => void

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NumberStyleOptions-onBlurIncrease?: () => void--><!--Device-NumberStyleOptions-onBlurIncrease?: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onFocusDecrease

```TypeScript
onFocusDecrease?: () => void
```

当前Counter组件的减小按钮获取焦点时触发的回调。

默认值：不触发减少按钮获取焦点时的回调。

值为undefined时，按默认值处理。

**类型：** () => void

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NumberStyleOptions-onFocusDecrease?: () => void--><!--Device-NumberStyleOptions-onFocusDecrease?: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onFocusIncrease

```TypeScript
onFocusIncrease?: () => void
```

当前Counter组件的增加按钮获取焦点时触发的回调。

默认值：不触发增加按钮获取焦点时的回调。

值为undefined时，按默认值处理。

**类型：** () => void

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-NumberStyleOptions-onFocusIncrease?: () => void--><!--Device-NumberStyleOptions-onFocusIncrease?: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

