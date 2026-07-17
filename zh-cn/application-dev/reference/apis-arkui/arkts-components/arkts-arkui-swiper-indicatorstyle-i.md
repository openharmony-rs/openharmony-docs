# IndicatorStyle

导航点样式。

> **说明：**

> 从API version 8开始支持，从API version 10开始废弃，建议使用[indicator](arkts-arkui-swiper-indicator-c.md)替代。

**起始版本：** 8

**废弃版本：** 10

**替代接口：** [Indicator](arkts-arkui-swiper-indicator-c.md)

<!--Device-unnamed-declare interface IndicatorStyle--><!--Device-unnamed-declare interface IndicatorStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## bottom

```TypeScript
bottom?: Length
```

设置导航点底部相对于Swiper的位置。

未设置top和bottom时，进行自适应大小布局，按照指示器本身大小和Swiper的大小，在交叉轴方向上，位于底部，效果与设置bottom=0一致

设置为0时：按照0位置布局计算

优先级：低于top属性

取值范围：[0,Swiper高度-导航点区域高度]，超出该范围时，取最近的边界值。

**类型：** Length

**起始版本：** 8

**废弃版本：** 10

**替代接口：** bottom

<!--Device-IndicatorStyle-bottom?: Length--><!--Device-IndicatorStyle-bottom?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color?: ResourceColor
```

设置导航点的颜色。

默认值：'#1A182431'，浅灰色。

**类型：** ResourceColor

**起始版本：** 8

**废弃版本：** 10

**替代接口：** [color](arkts-arkui-swiper-dotindicator-c.md#color-1)

<!--Device-IndicatorStyle-color?: ResourceColor--><!--Device-IndicatorStyle-color?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## left

```TypeScript
left?: Length
```

设置导航点左侧相对于Swiper的位置。

未设置left和right时，进行自适应大小布局，按照指示器本身大小和Swiper的大小在主轴方向上进行居中对齐

设置为0时：按照0位置布局计算

优先级：高于right属性

取值范围：[0,Swiper宽度-导航点区域宽度]，超出该范围时，取最近的边界值。

**类型：** Length

**起始版本：** 8

**废弃版本：** 10

**替代接口：** left

<!--Device-IndicatorStyle-left?: Length--><!--Device-IndicatorStyle-left?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## mask

```TypeScript
mask?: boolean
```

设置是否显示导航点蒙层样式。

true：显示导航点蒙层样式，false：不显示导航点蒙层样式。

默认值：false

**类型：** boolean

**起始版本：** 8

**废弃版本：** 10

**替代接口：** [mask](arkts-arkui-swiper-dotindicator-c.md#mask-1)

<!--Device-IndicatorStyle-mask?: boolean--><!--Device-IndicatorStyle-mask?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## right

```TypeScript
right?: Length
```

设置导航点右侧相对于Swiper的位置。

未设置left和right时，进行自适应大小布局，按照指示器本身大小和Swiper的大小在主轴方向上进行居中对齐

设置为0时：按照0位置布局计算

优先级：低于left属性

取值范围：[0,Swiper宽度-导航点区域宽度]，超出该范围时，取最近的边界值。

**类型：** Length

**起始版本：** 8

**废弃版本：** 10

**替代接口：** right

<!--Device-IndicatorStyle-right?: Length--><!--Device-IndicatorStyle-right?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedColor

```TypeScript
selectedColor?: ResourceColor
```

设置选中的导航点的颜色。

默认值：'#007DFF'，蓝色。

**类型：** ResourceColor

**起始版本：** 8

**废弃版本：** 10

**替代接口：** selectColor

<!--Device-IndicatorStyle-selectedColor?: ResourceColor--><!--Device-IndicatorStyle-selectedColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## size

```TypeScript
size?: Length
```

设置导航点的直径，不支持设置百分比。

默认值：6vp

**类型：** Length

**起始版本：** 8

**废弃版本：** 10

**替代接口：** [DotIndicator](arkts-arkui-swiper-dotindicator-c.md)

<!--Device-IndicatorStyle-size?: Length--><!--Device-IndicatorStyle-size?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## top

```TypeScript
top?: Length
```

设置导航点顶部相对于Swiper的位置。

未设置top和bottom时，进行自适应大小布局，按照指示器本身大小和Swiper的大小，在交叉轴方向上，位于底部，效果与设置bottom=0一致

设置为0时：按照0位置布局计算

优先级：高于bottom属性

取值范围：[0,Swiper高度-导航点区域高度]，超出该范围时，取最近的边界值。

**类型：** Length

**起始版本：** 8

**废弃版本：** 10

**替代接口：** top

<!--Device-IndicatorStyle-top?: Length--><!--Device-IndicatorStyle-top?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

