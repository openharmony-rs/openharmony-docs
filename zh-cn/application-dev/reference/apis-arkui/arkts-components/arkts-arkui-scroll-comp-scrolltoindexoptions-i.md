# ScrollToIndexOptions

```TypeScript
declare interface ScrollToIndexOptions
```

滑动到指定Index的参数选项。

**起始版本：** 12

<!--Device-unnamed-declare interface ScrollToIndexOptions--><!--Device-unnamed-declare interface ScrollToIndexOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## extraOffset

```TypeScript
extraOffset?: LengthMetrics
```

滚动到指定索引的额外偏移量。

**类型：** LengthMetrics

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

<!--Device-ScrollToIndexOptions-extraOffset?: LengthMetrics--><!--Device-ScrollToIndexOptions-extraOffset?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fastScroll

```TypeScript
fastScroll?: FastScrollMode
```

快速滚动模式，用于滚动到指定索引。当设置为NONE以外的值时，滚动动画将估算目标位置并在动画过程中跳过一些中间子组件。当scrollToIndex接口的smooth属性为true时，该参数才生效。默认值：FastScrollMode.NONE。

**类型：** [FastScrollMode](arkts-arkui-scroll-comp-fastscrollmode-e.md)

**起始版本：** 26.2.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.2.0开始，该接口支持在原子化服务中使用。

<!--Device-ScrollToIndexOptions-fastScroll?: FastScrollMode--><!--Device-ScrollToIndexOptions-fastScroll?: FastScrollMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
