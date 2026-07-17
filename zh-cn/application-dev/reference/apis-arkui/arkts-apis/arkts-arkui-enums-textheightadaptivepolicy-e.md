# TextHeightAdaptivePolicy

Enum of text height adaptation

**起始版本：** 10

<!--Device-unnamed-declare enum TextHeightAdaptivePolicy--><!--Device-unnamed-declare enum TextHeightAdaptivePolicy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## MAX_LINES_FIRST

```TypeScript
MAX_LINES_FIRST = 0
```

Priority is given to using the maxLines attribute to adapt the text height.If the layout size using the maxLines attribute exceeds the layout constraint, try reducing the font size to display more text.

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextHeightAdaptivePolicy-MAX_LINES_FIRST = 0--><!--Device-TextHeightAdaptivePolicy-MAX_LINES_FIRST = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## MIN_FONT_SIZE_FIRST

```TypeScript
MIN_FONT_SIZE_FIRST = 1
```

Priority is given to using the minFontSize attribute to adapt the text height.If the text can be layout in a single line using the minFontSize property, try increasing the font size and using the maximum possible font size.

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextHeightAdaptivePolicy-MIN_FONT_SIZE_FIRST = 1--><!--Device-TextHeightAdaptivePolicy-MIN_FONT_SIZE_FIRST = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## LAYOUT_CONSTRAINT_FIRST

```TypeScript
LAYOUT_CONSTRAINT_FIRST = 2
```

Priority is given to using the layout constraint to adapt the text height.If the layout size exceeds the layout constraint, try reducing the font size. If the layout size still exceeds the layout constraint after reducing the font size to minFontSize, remove the lines that exceed the layout constraint.

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TextHeightAdaptivePolicy-LAYOUT_CONSTRAINT_FIRST = 2--><!--Device-TextHeightAdaptivePolicy-LAYOUT_CONSTRAINT_FIRST = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

