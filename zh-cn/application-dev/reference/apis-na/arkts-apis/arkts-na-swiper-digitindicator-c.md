# DigitIndicator

Define DigitIndicator, the indicator type is digit.

**继承/实现关系：** DigitIndicator extends [Indicator](arkts-na-swiper-indicator-c.md#Indicator)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare class DigitIndicator--><!--Device-unnamed-export declare class DigitIndicator-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor()
```

DotIndicator的构造函数。 > **说明：** > > - 按压导航点时，导航点会放大至1.33倍显示，因此非按压态时导航点的可见范围边界至实际范围边界存在一定距离，该距离会随着itemWidth、itemHeight、selectedItemWidth、 > selectedItemHeight等参数变大而变大。 > > - 若页面数量较多、圆点导航点超出页面时，建议使用maxDisplayCount设置导航点显示个数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DigitIndicator-constructor()--><!--Device-DigitIndicator-constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## digitFont

```TypeScript
digitFont(value: Font | undefined): this
```

Swiper组件数字导航点的字体样式。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DigitIndicator-digitFont(value: Font | undefined): this--><!--Device-DigitIndicator-digitFont(value: Font | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Font](../../apis-arkui/arkts-apis/arkts-arkui-font-i.md) \| undefined | 是 | 设置Swiper组件数字导航点的字体样式。&lt;br/&gt;只支持Font中size和weight参数，family和style设置不生效。&lt;br/&gt;默认值：{ size:?14,?weight:?FontWeight.Normal?}&lt;br/&gt;取值为undefined时，按默认值处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## fontColor

```TypeScript
fontColor(value: ResourceColor | undefined): this
```

Swiper组件数字导航点的字体颜色。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DigitIndicator-fontColor(value: ResourceColor | undefined): this--><!--Device-DigitIndicator-fontColor(value: ResourceColor | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../../apis-arkui/arkts-apis/arkts-arkui-resourcecolor-t.md) \| undefined | 是 | 设置Swiper组件数字导航点的字体颜色。&lt;br/&gt;默认值：'#ff182431'，黑色。&lt;br/&gt;取值为undefined时，按默认值处理 。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## selectedDigitFont

```TypeScript
selectedDigitFont(value: Font | undefined): this
```

选中Swiper组件数字导航点的字体样式。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DigitIndicator-selectedDigitFont(value: Font | undefined): this--><!--Device-DigitIndicator-selectedDigitFont(value: Font | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Font](../../apis-arkui/arkts-apis/arkts-arkui-font-i.md) \| undefined | 是 | 设置选中Swiper组件数字导航点的字体样式。&lt;br/&gt;默认值：{?size:?14,?weight:?FontWeight.Normal?}&lt;br/&gt;取值为 undefined时，按默认值处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## selectedFontColor

```TypeScript
selectedFontColor(value: ResourceColor | undefined): this
```

选中Swiper组件数字导航点的字体颜色。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DigitIndicator-selectedFontColor(value: ResourceColor | undefined): this--><!--Device-DigitIndicator-selectedFontColor(value: ResourceColor | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../../apis-arkui/arkts-apis/arkts-arkui-resourcecolor-t.md) \| undefined | 是 | 设置选中Swiper组件数字导航点的字体颜色。&lt;br/&gt;默认值：'#ff182431'，黑色。&lt;br/&gt;取值为undefined时，按默认值 处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

