# SwiperContentWillScrollResult

滑动的相关信息，主要包括：当前页面对应的index、滑动方向上即将显示的页面index和此次滑动的位移。

**起始版本：** 15

<!--Device-unnamed-declare interface SwiperContentWillScrollResult--><!--Device-unnamed-declare interface SwiperContentWillScrollResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## comingIndex

```TypeScript
comingIndex: number
```

滑动方向上即将显示的页面index。

**类型：** number

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本15开始，该接口支持在ArkTS卡片中使用。

<!--Device-SwiperContentWillScrollResult-comingIndex: number--><!--Device-SwiperContentWillScrollResult-comingIndex: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## currentIndex

```TypeScript
currentIndex: number
```

当前页面对应的index。在一次跟手滑动过程中，只要手指未离开屏幕，该值将保持不变，即使该页面已完全移出视窗，如在涉及多个页面的场景中。

**类型：** number

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本15开始，该接口支持在ArkTS卡片中使用。

<!--Device-SwiperContentWillScrollResult-currentIndex: number--><!--Device-SwiperContentWillScrollResult-currentIndex: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset: number
```

此次滑动的位移，带有符号，正负分别指示不同的翻页方向。正数表示从index=1向index=0翻页，负数表示从index=0向index=1翻页。

在手指滑动的场景中，该值为滑动事件中每帧传递下来的偏移量。在滚动鼠标滚轮和使用键盘方向键导航的场景中，该值代表即将翻页的距离。

**类型：** number

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本15开始，该接口支持在ArkTS卡片中使用。

<!--Device-SwiperContentWillScrollResult-offset: number--><!--Device-SwiperContentWillScrollResult-offset: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

