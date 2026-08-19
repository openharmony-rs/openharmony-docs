# IndicatorComponentController

Indicator组件的控制器，可以将此对象绑定至Indicator组件来控制翻页。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class IndicatorComponentController--><!--Device-unnamed-export declare class IndicatorComponentController-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## changeIndex

```TypeScript
changeIndex(index: int | undefined, useAnimation?: boolean): void
```

翻至指定页面。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IndicatorComponentController-changeIndex(index: int | undefined, useAnimation?: boolean): void--><!--Device-IndicatorComponentController-changeIndex(index: int | undefined, useAnimation?: boolean): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int \| undefined | 是 | 指定页面在Swiper中的索引值。 |
| useAnimation | boolean | 否 | 设置翻至指定页面时是否有动效，true表示有动效，false表示没有动效。<br/>默认值：false。 |

## constructor

```TypeScript
constructor()
```

IndicatorComponentController的构造函数。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IndicatorComponentController-constructor()--><!--Device-IndicatorComponentController-constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## showNext

```TypeScript
showNext(): void
```

跳转到下一导航点。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IndicatorComponentController-showNext(): void--><!--Device-IndicatorComponentController-showNext(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## showPrevious

```TypeScript
showPrevious(): void
```

跳转到上一导航点。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IndicatorComponentController-showPrevious(): void--><!--Device-IndicatorComponentController-showPrevious(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

