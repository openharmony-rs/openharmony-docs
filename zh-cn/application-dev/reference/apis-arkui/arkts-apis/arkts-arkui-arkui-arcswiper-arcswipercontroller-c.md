# ArcSwiperController

ArcSwiper容器组件的控制器，可以将此对象绑定至ArcSwiper组件，可以通过它控制翻页。

**起始版本：** 18

<!--Device-unnamed-export class ArcSwiperController--><!--Device-unnamed-export class ArcSwiperController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## 导入模块

```TypeScript
import { ArcSwiperAttribute, ArcSwiper, ArcDirection, ArcSwiperController, ArcDotIndicator } from '@kit.ArkUI';
```

<a id="constructor"></a>
## constructor

```TypeScript
constructor()
```

ArcSwiperController的构造函数。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcSwiperController-constructor()--><!--Device-ArcSwiperController-constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

<a id="finishanimation"></a>
## finishAnimation

```TypeScript
finishAnimation(handler?: FinishAnimationHandler)
```

停止播放动画。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcSwiperController-finishAnimation(handler?: FinishAnimationHandler)--><!--Device-ArcSwiperController-finishAnimation(handler?: FinishAnimationHandler)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| handler | [FinishAnimationHandler](arkts-arkui-finishanimationhandler-t.md) | 否 | 动画结束的回调。<br>默认值：不传入的情况，无回调 |

<a id="shownext"></a>
## showNext

```TypeScript
showNext()
```

翻至下一页。翻页带动效切换过程，时长通过[duration](arkts-arkui-arkui-arcswiper-arcswiperattribute-c.md#duration-1)指定。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcSwiperController-showNext()--><!--Device-ArcSwiperController-showNext()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

<a id="showprevious"></a>
## showPrevious

```TypeScript
showPrevious()
```

翻至上一页。翻页带动效切换过程，时长通过[duration](arkts-arkui-arkui-arcswiper-arcswiperattribute-c.md#duration-1)指定。

**起始版本：** 18

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-ArcSwiperController-showPrevious()--><!--Device-ArcSwiperController-showPrevious()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

