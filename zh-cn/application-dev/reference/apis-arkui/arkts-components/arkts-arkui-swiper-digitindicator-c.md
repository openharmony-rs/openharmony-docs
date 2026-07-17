# DigitIndicator

构造数字指示器的样式，继承自[Indicator](arkts-arkui-swiper-indicator-c.md)。

> **说明：**

> 按组翻页时，数字导航点显示的子节点数量不包括占位节点。

> 数字导航点文本最大的字体缩放倍数[maxFontScale](TextAttribute#maxFontScale)为2。

> 页码的镜像显示依据为系统的RTL状态。

**继承/实现关系：** DigitIndicator extends [Indicator<DigitIndicator>](Indicator<DigitIndicator>)

**起始版本：** 10

<!--Device-unnamed-declare class DigitIndicator extends Indicator<DigitIndicator>--><!--Device-unnamed-declare class DigitIndicator extends Indicator<DigitIndicator>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor()
```

DotIndicator的构造函数。

> **说明：**

> - 按压导航点时，导航点会放大至1.33倍显示，因此非按压态时导航点的可见范围边界至实际范围边界存在一定距离，该距离会随着itemWidth、itemHeight、selectedItemWidth、  
> selectedItemHeight等参数变大而变大。  
>  
> - 若页面数量较多、圆点导航点超出页面时，建议使用maxDisplayCount设置导航点显示个数。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-DigitIndicator-constructor()--><!--Device-DigitIndicator-constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## digitFont

```TypeScript
digitFont(value: Font): DigitIndicator
```

Swiper组件数字导航点的字体样式。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-DigitIndicator-digitFont(value: Font): DigitIndicator--><!--Device-DigitIndicator-digitFont(value: Font): DigitIndicator-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Font](../arkts-apis/arkts-arkui-arkui-uicontext-font-c.md) | 是 | 设置Swiper组件数字导航点的字体样式。<br/>只支持Font中size和weight参数，family和style设置不生效。<br/>默认值：<br/>{ size: 14, weight: FontWeight.Normal } |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DigitIndicator](arkts-arkui-swiper-digitindicator-c.md) | 返回当前数字指示器。 |

## fontColor

```TypeScript
fontColor(value: ResourceColor): DigitIndicator
```

Swiper组件数字导航点的字体颜色。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-DigitIndicator-fontColor(value: ResourceColor): DigitIndicator--><!--Device-DigitIndicator-fontColor(value: ResourceColor): DigitIndicator-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 设置Swiper组件数字导航点的字体颜色。<br/>默认值：'#ff182431' |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DigitIndicator](arkts-arkui-swiper-digitindicator-c.md) | 返回当前数字指示器。 |

## selectedDigitFont

```TypeScript
selectedDigitFont(value: Font): DigitIndicator
```

选中Swiper组件数字导航点的字体样式。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-DigitIndicator-selectedDigitFont(value: Font): DigitIndicator--><!--Device-DigitIndicator-selectedDigitFont(value: Font): DigitIndicator-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Font](../arkts-apis/arkts-arkui-arkui-uicontext-font-c.md) | 是 | 设置选中Swiper组件数字导航点的字体样式。<br/>默认值：<br/>{ size: 14, weight: FontWeight.Normal } |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DigitIndicator](arkts-arkui-swiper-digitindicator-c.md) | 返回当前数字指示器。 |

## selectedFontColor

```TypeScript
selectedFontColor(value: ResourceColor): DigitIndicator
```

选中Swiper组件数字导航点的字体颜色。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-DigitIndicator-selectedFontColor(value: ResourceColor): DigitIndicator--><!--Device-DigitIndicator-selectedFontColor(value: ResourceColor): DigitIndicator-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 设置选中Swiper组件数字导航点的字体颜色。<br/>默认值：'#ff182431' |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DigitIndicator](arkts-arkui-swiper-digitindicator-c.md) | 返回当前数字指示器。 |

