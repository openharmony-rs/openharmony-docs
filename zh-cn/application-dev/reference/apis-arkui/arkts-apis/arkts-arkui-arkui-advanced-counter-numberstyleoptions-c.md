# NumberStyleOptions

NumberStyleOptions定义了列表型和紧凑型Counter的属性和事件。继承于[InlineStyleOptions](arkts-arkui-arkui-advanced-counter-inlinestyleoptions-c.md)，包含该接口所有属性。本节仅展示新增属性，继承属性请参见父接口。

**继承/实现关系：** NumberStyleOptions extends [InlineStyleOptions](arkts-arkui-arkui-advanced-counter-inlinestyleoptions-c.md)

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
import { CounterComponent, CounterOptions, CounterType, DateData } from '@kit.ArkUI';
```

## onBlurDecrease

```TypeScript
onBlurDecrease?: () => void
```

当前Counter组件的减少按钮失去焦点时触发的回调。使用场景：当需要在减少按钮失焦时执行自定义操作（如验证输入、保存状态等）时传入此回调。默认值：不触发减少按钮失去焦点时的回调。值为undefined时，按默认值处理。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onBlurIncrease

```TypeScript
onBlurIncrease?: () => void
```

当前Counter组件的增加按钮失去焦点时触发的回调。使用场景：当需要在增加按钮失焦时执行自定义操作（如验证输入、保存状态等）时传入此回调。默认值：不触发增加按钮失去焦点时的回调。值为undefined时，按默认值处理。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onFocusDecrease

```TypeScript
onFocusDecrease?: () => void
```

当前Counter组件的减少按钮获取焦点时触发的回调。使用场景：当需要在减少按钮获焦时执行自定义操作（如改变样式、记录日志等）时传入此回调。默认值：不触发减少按钮获取焦点时的回调。值为undefined时，按默认值处理。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onFocusIncrease

```TypeScript
onFocusIncrease?: () => void
```

当前Counter组件的增加按钮获取焦点时触发的回调。使用场景：当需要在增加按钮获焦时执行自定义操作（如改变样式、记录日志等）时传入此回调。默认值：不触发增加按钮获取焦点时的回调。值为undefined时，按默认值处理。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## label

```TypeScript
label?: ResourceStr
```

设置Counter的说明文本。使用场景：当需要在Counter旁边显示说明文字（如'价格'、'数量'等）时传入此参数。默认值：''值为undefined时，按默认值处理。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
