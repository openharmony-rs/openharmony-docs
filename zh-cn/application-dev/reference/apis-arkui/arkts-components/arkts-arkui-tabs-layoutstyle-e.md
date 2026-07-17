# LayoutStyle

[Scrollable](TabsAttribute#barMode(value: BarMode, options?: ScrollableBarModeOptions))模式下不滚动时的页签排布方式枚举。

**起始版本：** 10

<!--Device-unnamed-declare enum LayoutStyle--><!--Device-unnamed-declare enum LayoutStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ALWAYS_CENTER

```TypeScript
ALWAYS_CENTER = 0
```

当页签内容超过TabBar宽度时，TabBar可滚动。

当页签内容不超过TabBar宽度时，TabBar不可滚动，页签紧凑居中。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LayoutStyle-ALWAYS_CENTER = 0--><!--Device-LayoutStyle-ALWAYS_CENTER = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## ALWAYS_AVERAGE_SPLIT

```TypeScript
ALWAYS_AVERAGE_SPLIT = 1
```

当页签内容超过TabBar宽度时，TabBar可滚动。

当页签内容不超过TabBar宽度时，TabBar不可滚动，且所有页签平均分配TabBar宽度。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LayoutStyle-ALWAYS_AVERAGE_SPLIT = 1--><!--Device-LayoutStyle-ALWAYS_AVERAGE_SPLIT = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SPACE_BETWEEN_OR_CENTER

```TypeScript
SPACE_BETWEEN_OR_CENTER = 2
```

当页签内容超过TabBar宽度时，TabBar可滚动。

当页签内容不超过TabBar宽度但超过TabBar宽度一半时，TabBar不可滚动，页签紧凑居中。

当页签内容不超过TabBar宽度一半时，TabBar不可滚动，保证页签居中排列在TabBar宽度一半，且间距相同。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-LayoutStyle-SPACE_BETWEEN_OR_CENTER = 2--><!--Device-LayoutStyle-SPACE_BETWEEN_OR_CENTER = 2-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

