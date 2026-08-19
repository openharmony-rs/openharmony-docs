# SwiperContentWillScrollResult

The result of swiper ContentWillScrollCallback.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface SwiperContentWillScrollResult--><!--Device-unnamed-export declare interface SwiperContentWillScrollResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## comingIndex

```TypeScript
comingIndex: int
```

滑动方向上即将显示的页面index。 取值范围为全体整数。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwiperContentWillScrollResult-comingIndex: int--><!--Device-SwiperContentWillScrollResult-comingIndex: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## currentIndex

```TypeScript
currentIndex: int
```

当前页面对应的index。在一次跟手滑动过程中，只要手指未离开屏幕，该值将保持不变，即使该页面已完全移出视窗，如在涉及多个页面的场景中。 取值范围为全体整数。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwiperContentWillScrollResult-currentIndex: int--><!--Device-SwiperContentWillScrollResult-currentIndex: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offset

```TypeScript
offset: double
```

此次滑动的位移，带有符号，正负分别指示不同的翻页方向。正数表示从index=1向index=0翻页，负数表示从index=0向index=1翻页。 在手指滑动的场景中，该值为滑动事件中每帧传递下来的偏移量。在滚动鼠标滚轮和使用键盘方向键导航的场景中，该值代表即将翻页的距离。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwiperContentWillScrollResult-offset: double--><!--Device-SwiperContentWillScrollResult-offset: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

