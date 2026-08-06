# ArcSwiperController

ArcSwiper容器组件的控制器，可以将此对象绑定至ArcSwiper组件，实现控制ArcSwiper翻页等功能。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export declare class ArcSwiperController--><!--Device-unnamed-export declare class ArcSwiperController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## constructor

```TypeScript
constructor()
```

ArcSwiperController的构造函数。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArcSwiperController-constructor()--><!--Device-ArcSwiperController-constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## finishAnimation

```TypeScript
finishAnimation(handler?: FinishAnimationHandler): void
```

停止播放动画。默认无回调。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArcSwiperController-finishAnimation(handler?: FinishAnimationHandler): void--><!--Device-ArcSwiperController-finishAnimation(handler?: FinishAnimationHandler): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | 动画结束的回调。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_默认值：不传入时无回调 |

## showNext

```TypeScript
showNext(): void
```

翻至下一页。翻页带动效切换过程，时长通过[duration]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_指定。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArcSwiperController-showNext(): void--><!--Device-ArcSwiperController-showNext(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## showPrevious

```TypeScript
showPrevious(): void
```

翻至上一页。翻页带动效切换过程，时长通过[duration]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_指定。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArcSwiperController-showPrevious(): void--><!--Device-ArcSwiperController-showPrevious(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

