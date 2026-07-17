# DotIndicator

构造圆点指示器的样式，继承自[Indicator](arkts-arkui-swiper-indicator-c.md)。

**继承/实现关系：** DotIndicator extends [Indicator<DotIndicator>](Indicator<DotIndicator>)

**起始版本：** 10

<!--Device-unnamed-declare class DotIndicator extends Indicator<DotIndicator>--><!--Device-unnamed-declare class DotIndicator extends Indicator<DotIndicator>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color(value: ResourceColor): DotIndicator
```

Swiper组件圆点导航指示器的颜色。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-DotIndicator-color(value: ResourceColor): DotIndicator--><!--Device-DotIndicator-color(value: ResourceColor): DotIndicator-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 设置Swiper组件圆点导航指示器的颜色。<br/>默认值：'#1A182431'，浅灰色。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DotIndicator](arkts-arkui-swiper-dotindicator-c.md) | 返回当前圆点指示器。 |

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

<!--Device-DotIndicator-constructor()--><!--Device-DotIndicator-constructor()-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## indicatorIcon

```TypeScript
indicatorIcon(iconList: Array<IndicatorIconInfo>): DotIndicator
```

设置导航点图标。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-DotIndicator-indicatorIcon(iconList: Array<IndicatorIconInfo>): DotIndicator--><!--Device-DotIndicator-indicatorIcon(iconList: Array<IndicatorIconInfo>): DotIndicator-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| iconList | [Array](../../apis-arkts/arkts-apis/arkts-arkts-collections-array-c.md)<IndicatorIconInfo> | 是 | 需要设置的导航点索引。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DotIndicator](arkts-arkui-swiper-dotindicator-c.md) | 返回DotIndicator。 |

## itemHeight

```TypeScript
itemHeight(value: Length): DotIndicator
```

Swiper组件圆点导航指示器的高。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-DotIndicator-itemHeight(value: Length): DotIndicator--><!--Device-DotIndicator-itemHeight(value: Length): DotIndicator-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | 是 | 设置Swiper组件圆点导航指示器的高，不支持设置百分比。<br/>默认值：6<br/>单位：vp<br/>取值范围：(0, +∞) |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DotIndicator](arkts-arkui-swiper-dotindicator-c.md) | 返回当前圆点指示器。 |

## itemWidth

```TypeScript
itemWidth(value: Length): DotIndicator
```

Swiper组件圆点导航指示器的宽。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-DotIndicator-itemWidth(value: Length): DotIndicator--><!--Device-DotIndicator-itemWidth(value: Length): DotIndicator-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | 是 | 设置Swiper组件圆点导航指示器的宽，不支持设置百分比。<br/>默认值：6<br/>单位：vp<br/>取值范围：(0, +∞) |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DotIndicator](arkts-arkui-swiper-dotindicator-c.md) | 返回当前圆点指示器。 |

## mask

```TypeScript
mask(value: boolean): DotIndicator
```

是否显示Swiper组件圆点导航指示器的蒙版样式。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-DotIndicator-mask(value: boolean): DotIndicator--><!--Device-DotIndicator-mask(value: boolean): DotIndicator-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 设置是否显示Swiper组件圆点导航指示器的蒙版样式。true为显示Swiper组件圆点导航指示器的蒙版样式，false为不显示。<br/>默认值：false |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DotIndicator](arkts-arkui-swiper-dotindicator-c.md) | 返回当前圆点指示器。 |

## maxDisplayCount

```TypeScript
maxDisplayCount(maxDisplayCount: number): DotIndicator
```

圆点导航点指示器样式下，导航点显示个数最大值。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DotIndicator-maxDisplayCount(maxDisplayCount: number): DotIndicator--><!--Device-DotIndicator-maxDisplayCount(maxDisplayCount: number): DotIndicator-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| maxDisplayCount | number | 是 | 设置圆点导航点指示器样式下，导航点显示个数最大值，当实际导航点个数大于最大导航点个数时，会生效超长效果样式，样式如[示例5](../../../../reference/apis-arkui/arkui-ts/ts-container-swiper.md#示例5设置圆点导航点超长显示)所示。<br/>默认值：这个属性没有默认值，如果设置异常值那等同于没有超长显示效果。<br/>取值范围：[6, 9]<br/>**说明：** <br/>1、超长显示场景，目前暂时不支持交互功能（包括：手指点击拖拽、鼠标操作等）。<br/>2、在超长显示场景下，中间页面对应的选中导航点的位置，并不是完全固定的，取决于之前的翻页操作序列。<br/>3、当前仅支持displayCount为1的场景。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DotIndicator](arkts-arkui-swiper-dotindicator-c.md) | 返回当前圆点指示器。 |

## selectedColor

```TypeScript
selectedColor(value: ResourceColor): DotIndicator
```

选中Swiper组件圆点导航指示器的颜色。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-DotIndicator-selectedColor(value: ResourceColor): DotIndicator--><!--Device-DotIndicator-selectedColor(value: ResourceColor): DotIndicator-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 设置选中Swiper组件圆点导航指示器的颜色。<br/>默认值：'#007DFF'，蓝色。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DotIndicator](arkts-arkui-swiper-dotindicator-c.md) | 返回当前圆点指示器。 |

## selectedItemHeight

```TypeScript
selectedItemHeight(value: Length): DotIndicator
```

选中Swiper组件圆点导航指示器的高。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-DotIndicator-selectedItemHeight(value: Length): DotIndicator--><!--Device-DotIndicator-selectedItemHeight(value: Length): DotIndicator-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | 是 | 设置选中Swiper组件圆点导航指示器的高，不支持设置百分比。<br/>默认值：6<br/>单位：vp<br/>取值范围：(0, +∞) |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DotIndicator](arkts-arkui-swiper-dotindicator-c.md) | 返回当前圆点指示器。 |

## selectedItemWidth

```TypeScript
selectedItemWidth(value: Length): DotIndicator
```

选中Swiper组件圆点导航指示器的宽。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-DotIndicator-selectedItemWidth(value: Length): DotIndicator--><!--Device-DotIndicator-selectedItemWidth(value: Length): DotIndicator-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | 是 | 设置选中Swiper组件圆点导航指示器的宽，不支持设置百分比。<br/>默认值：6<br/>单位：vp<br/>取值范围：(0, +∞) |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DotIndicator](arkts-arkui-swiper-dotindicator-c.md) | 返回当前圆点指示器。 |

## space

```TypeScript
space(space: LengthMetrics): DotIndicator
```

设置Swiper圆点导航点间距。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本19开始，该接口支持在ArkTS卡片中使用。

<!--Device-DotIndicator-space(space: LengthMetrics): DotIndicator--><!--Device-DotIndicator-space(space: LengthMetrics): DotIndicator-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| space | [LengthMetrics](../arkts-apis/arkts-arkui-lengthmetrics-t.md) | 是 | 设置圆点导航点间距，不支持设置百分比。<br/>默认值：PC/2in1设备上为10，其他设备为8。<br/>单位：vp<br/>取值范围：[0, +∞) |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DotIndicator](arkts-arkui-swiper-dotindicator-c.md) | 返回当前圆点指示器。 |

