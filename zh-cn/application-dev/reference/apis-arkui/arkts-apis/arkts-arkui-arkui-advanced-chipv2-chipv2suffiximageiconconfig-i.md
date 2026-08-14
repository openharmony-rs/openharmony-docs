# ChipV2SuffixImageIconConfig

ChipV2SuffixImageIconConfig定义后缀图标的属性配置。 继承自[ChipV2ImageIconConfig](arkts-arkui-arkui-advanced-chipv2-chipv2imageiconconfig-i.md#ChipV2ImageIconConfig)和[ChipV2AccessibilityConfig](arkts-arkui-arkui-advanced-chipv2-chipv2accessibilityconfig-i.md#ChipV2AccessibilityConfig)。

**继承/实现关系：** ChipV2SuffixImageIconConfig extends [ChipV2ImageIconConfig](arkts-arkui-arkui-advanced-chipv2-chipv2imageiconconfig-i.md#ChipV2ImageIconConfig), [ChipV2AccessibilityConfig](arkts-arkui-arkui-advanced-chipv2-chipv2accessibilityconfig-i.md#ChipV2AccessibilityConfig)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-export interface ChipV2SuffixImageIconConfig--><!--Device-unnamed-export interface ChipV2SuffixImageIconConfig-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## action

```TypeScript
action?: VoidCallback
```

后缀图标点击事件回调函数。当需要为后缀图标绑定点击事件并执行自定义操作时传入此回调函数（如触发特定功能、打开弹窗等）。点击后缀图标时调用此回调函数。 默认值：undefined，不设定后缀图标事件。不传入或传入undefined时，点击后缀图标无自定义响应。

**类型：** VoidCallback

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ChipV2SuffixImageIconConfig-action?: VoidCallback--><!--Device-ChipV2SuffixImageIconConfig-action?: VoidCallback-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

