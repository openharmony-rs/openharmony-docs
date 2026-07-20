# IndicatorComponentController

Indicator组件的控制器，可以将此对象绑定至Indicator组件来控制翻页。

**起始版本：** 15

<!--Device-unnamed-declare class IndicatorComponentController--><!--Device-unnamed-declare class IndicatorComponentController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="changeindex"></a>
## changeIndex

```TypeScript
changeIndex(index: number, useAnimation?: boolean):void
```

翻至指定导航点。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本15开始，该接口支持在ArkTS卡片中使用。

<!--Device-IndicatorComponentController-changeIndex(index: number, useAnimation?: boolean):void--><!--Device-IndicatorComponentController-changeIndex(index: number, useAnimation?: boolean):void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 | 指定导航点在Swiper中的索引值。<br/>**说明：** <br/>设置的值小于0或大于最大导航点索引时，取0。 |
| useAnimation | boolean | 否 | 设置翻至指定导航点时是否有动效，true表示有动效，false表示没有动效。<br/>默认值：false。 |

<a id="constructor"></a>
## constructor

```TypeScript
constructor()
```

IndicatorComponentController的构造函数。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本15开始，该接口支持在ArkTS卡片中使用。

<!--Device-IndicatorComponentController-constructor()--><!--Device-IndicatorComponentController-constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="shownext"></a>
## showNext

```TypeScript
showNext():void
```

跳转到下一导航点。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本15开始，该接口支持在ArkTS卡片中使用。

<!--Device-IndicatorComponentController-showNext():void--><!--Device-IndicatorComponentController-showNext():void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="showprevious"></a>
## showPrevious

```TypeScript
showPrevious():void
```

跳转到上一导航点。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本15开始，该接口支持在ArkTS卡片中使用。

<!--Device-IndicatorComponentController-showPrevious():void--><!--Device-IndicatorComponentController-showPrevious():void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

