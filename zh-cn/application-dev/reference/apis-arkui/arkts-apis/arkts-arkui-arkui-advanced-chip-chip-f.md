# Chip

## 导入模块

```TypeScript
import { Chip, ChipOptions, ChipSize, IconCommonOptions, LabelMarginOptions, LabelOptions, PrefixIconOptions, SuffixIconOptions, ChipSymbolGlyphOptions, AccessibilitySelectedType, AccessibilityOptions, CloseOptions, ChipSuffixSymbolGlyphOptions } from '@kit.ArkUI';
```

## Chip

```TypeScript
export declare function Chip(options: ChipOptions): void
```

Chip组件用于标签展示和交互场景，支持自定义样式、图标、激活态等功能，适用于搜索框历史记录、邮件发送列表等场景，可快速实现标签的创建、删除和交互能力。

> **说明：** 
> 
> - 如果Chip设置[通用属性](../arkts-components/arkts-arkui-commonmethod-c.md)或[通用事件](../arkts-components/arkts-arkui-commonmethod-c.md)，编译工具链会额外生成节点__Common__，并将通用属性或通用事件挂载在__Common__上，而不是直接应用到Chip本身。这可能导致开发者设置的通用属性或通用事件不生效或不符合预期，因此，不建议Chip设置通用属性和通用事件。

## 导入模块

```ts
import { Chip, ChipOptions, ChipSize } from '@kit.ArkUI';
```

## 子组件

无

**起始版本：** 11

**装饰器类型：** @Builder

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [ChipOptions](arkts-arkui-arkui-advanced-chip-chipoptions-i.md) | 是 | 定义Chip组件的参数，包括尺寸、启用状态、激活态、前缀/后缀图标、文本内容、背景颜色、圆角、无障碍属性等，用于自定义Chip组件的样式和行为。 |
