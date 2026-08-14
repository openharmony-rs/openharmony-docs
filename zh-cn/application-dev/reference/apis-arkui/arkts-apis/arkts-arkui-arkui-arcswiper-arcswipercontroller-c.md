# ArcSwiperController

ArcSwiper容器组件的控制器，可以将此对象绑定至ArcSwiper组件，可以通过它控制翻页。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

<!--Device-unnamed-export class ArcSwiperController--><!--Device-unnamed-export class ArcSwiperController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## constructor

```TypeScript
constructor()
```

ArcSwiperController的构造函数。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcSwiperController-constructor()--><!--Device-ArcSwiperController-constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## finishAnimation

```TypeScript
finishAnimation(handler?: FinishAnimationHandler)
```

停止播放动画。通过此方法控制翻页时，effectMode设置的回弹效果不生效。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcSwiperController-finishAnimation(handler?: FinishAnimationHandler)--><!--Device-ArcSwiperController-finishAnimation(handler?: FinishAnimationHandler)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | [FinishAnimationHandler](../../apis-na/arkts-apis/arkts-na-finishanimationhandler-t.md) | 否 | 动画结束的回调。&lt;br&gt;默认值：不传入时无回调。 |

## showNext

```TypeScript
showNext()
```

翻至下一页。翻页带动效切换过程，时长通过[duration](../../apis-na/arkts-apis/arkts-na-arkui-arcswiper-arcswiperattribute-i.md#duration)指定。通过此方法控制翻页时，effectMode设置的回弹效果不生效。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcSwiperController-showNext()--><!--Device-ArcSwiperController-showNext()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## showPrevious

```TypeScript
showPrevious()
```

翻至上一页。翻页带动效切换过程，时长通过[duration](../../apis-na/arkts-apis/arkts-na-arkui-arcswiper-arcswiperattribute-i.md#duration)指定。通过此方法控制翻页时，effectMode设置的回弹效果不生效。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**废弃版本：** -1

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcSwiperController-showPrevious()--><!--Device-ArcSwiperController-showPrevious()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

