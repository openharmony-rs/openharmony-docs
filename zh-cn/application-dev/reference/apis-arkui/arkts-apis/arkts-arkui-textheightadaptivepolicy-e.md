# TextHeightAdaptivePolicy

```TypeScript
declare enum TextHeightAdaptivePolicy
```

文本自适应布局调整字号的方式。

**起始版本：** 10

<!--Device-unnamed-declare enum TextHeightAdaptivePolicy--><!--Device-unnamed-declare enum TextHeightAdaptivePolicy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## LAYOUT_CONSTRAINT_FIRST

```TypeScript
LAYOUT_CONSTRAINT_FIRST = 2
```

设置文本高度自适应方式为以布局约束（高度）优先。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

<!--Device-TextHeightAdaptivePolicy-LAYOUT_CONSTRAINT_FIRST = 2--><!--Device-TextHeightAdaptivePolicy-LAYOUT_CONSTRAINT_FIRST = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## MAX_LINES_FIRST

```TypeScript
MAX_LINES_FIRST = 0
```

设置文本高度自适应方式为以[maxLines](../arkts-components/arkts-arkui-textarea-comp-attribute.md#maxlines1)优先。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

<!--Device-TextHeightAdaptivePolicy-MAX_LINES_FIRST = 0--><!--Device-TextHeightAdaptivePolicy-MAX_LINES_FIRST = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## MIN_FONT_SIZE_FIRST

```TypeScript
MIN_FONT_SIZE_FIRST = 1
```

设置文本高度自适应方式为以缩小字体优先。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

<!--Device-TextHeightAdaptivePolicy-MIN_FONT_SIZE_FIRST = 1--><!--Device-TextHeightAdaptivePolicy-MIN_FONT_SIZE_FIRST = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
