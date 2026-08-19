# Indicator

Defines the indicator class.

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare class Indicator--><!--Device-unnamed-export declare class Indicator-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## bottom

```TypeScript
bottom(value: Length | undefined): this
```

导航点底部相对于Swiper的位置。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Indicator-bottom(value: Length | undefined): this--><!--Device-Indicator-bottom(value: Length | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../../apis-arkui/arkts-apis/arkts-arkui-length-t.md) \| undefined | 是 | 设置导航点底部相对于Swiper的位置。<br/>未设置top和bottom时，进行自适应大小布局，按照指示器本身大小和Swiper的大小，在交叉轴方向上 ，位于底部，效果与设置bottom=0一致。<br/>设置为0时：按照0位置布局计算。<br/>优先级：低于top属性。<br/>取值范围：[0,Swiper高度-导航点区域高度]，超出该范围时，取最近的边界值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## bottom

```TypeScript
bottom(bottom: LengthMetrics | Length | undefined, ignoreSize: boolean): this
```

导航点底部相对于Swiper的位置，并可通过ignoreSize属性忽略导航点大小。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Indicator-bottom(bottom: LengthMetrics | Length | undefined, ignoreSize: boolean): this--><!--Device-Indicator-bottom(bottom: LengthMetrics | Length | undefined, ignoreSize: boolean): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bottom | [LengthMetrics](../../apis-arkui/arkts-apis/arkts-arkui-lengthmetrics-t.md) \| [Length](../../apis-arkui/arkts-apis/arkts-arkui-length-t.md) \| undefined | 是 | 设置导航点底部相对于Swiper的位置。<br/>未设置top和bottom时，进行自适应大小布局，按照指示器本身大小和 Swiper的大小，在交叉轴方向上，位于底部，效果与设置bottom=0一致。<br/>设置为0时：按照0位置布局计算。<br/>优先级：低于top属性。<br/>取值范围：[0,Swiper高度-导航点区域高度]，超出该 范围时，取最近的边界值。 |
| ignoreSize | boolean | 是 | 设置是否忽略导航点本身大小，默认false。<br/>true表示可以将导航点更靠近Swiper底部；false表示忽略导航点本身大小。<br/>使用方法可以参考 示例9演示导航点space与bottom 。<br/> 说明：[数字导航点](arkts-na-swiper-digitindicator-c.md)ignoreSize属性，不生效的场景如下：<br/> ? 当 [vertical](arkts-na-swiper-swiperattribute-i.md#vertical) 设置为false，且bottom > 0。<br/> ? 当 [vertical](arkts-na-swiper-swiperattribute-i.md#vertical) 设置为true时：<br/>1、bottom > 0 时。<br/> 2、bottom设为undefined。 <br/> 3、 isSidebarMiddle设置为false时。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## digit

```TypeScript
static digit(): DigitIndicator
```

返回一个DigitIndicator对象。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Indicator-static digit(): DigitIndicator--><!--Device-Indicator-static digit(): DigitIndicator-End-->

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DigitIndicator](arkts-na-swiper-digitindicator-c.md) | 数字指示器对象，用于设置Swiper组件的数字导航样式。 |

## dot

```TypeScript
static dot(): DotIndicator
```

返回一个DotIndicator对象。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Indicator-static dot(): DotIndicator--><!--Device-Indicator-static dot(): DotIndicator-End-->

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DotIndicator](arkts-na-swiper-dotindicator-c.md) | 圆点指示器对象，用于设置Swiper组件的圆点导航样式。 |

## end

```TypeScript
end(value: LengthMetrics | undefined): this
```

在RTL模式下为导航点距离Swiper组件左边的距离，在LTR模式下为导航点距离Swiper组件右边的距离。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Indicator-end(value: LengthMetrics | undefined): this--><!--Device-Indicator-end(value: LengthMetrics | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [LengthMetrics](../../apis-arkui/arkts-apis/arkts-arkui-lengthmetrics-t.md) \| undefined | 是 | 设置在RTL模式下为导航点距离Swiper组件左边的距离，在LTR模式下为导航点距离Swiper组件右边的距离。<br/>默认值：0&lt;br/ &gt;单位：vp<br/>取值范围：[0, Swiper宽度-导航点区域宽度]，超出该范围时，取最近的边界值。<br/>取值为undefined时，按默认值处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## left

```TypeScript
left(value: Length | undefined): this
```

导航点左侧相对于Swiper的位置。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Indicator-left(value: Length | undefined): this--><!--Device-Indicator-left(value: Length | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../../apis-arkui/arkts-apis/arkts-arkui-length-t.md) \| undefined | 是 | 设置导航点左侧相对于Swiper的位置。<br/>未设置left和right时，进行自适应大小布局，按照指示器本身大小和Swiper的大小在主轴方向上进行 居中对齐。<br/>设置为0时：按照0位置布局计算。<br/>优先级：高于right属性。<br/>取值范围：[0,Swiper宽度-导航点区域宽度]，超出该范围时，取最近的边界值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## right

```TypeScript
right(value: Length | undefined): this
```

导航点右侧相对于Swiper的位置。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Indicator-right(value: Length | undefined): this--><!--Device-Indicator-right(value: Length | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../../apis-arkui/arkts-apis/arkts-arkui-length-t.md) \| undefined | 是 | 设置导航点右侧相对于Swiper的位置。<br/>未设置left和right时，进行自适应大小布局，按照指示器本身大小和Swiper的大小在主轴方向上进行 居中对齐。<br/>设置为0时：按照0位置布局计算。<br/>优先级：低于left属性。<br/>取值范围：[0,Swiper宽度-导航点区域宽度]，超出该范围 时，取最近的边界值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## start

```TypeScript
start(value: LengthMetrics | undefined): this
```

在[RTL](../../apis-arkui/arkts-apis/arkts-arkui-layoutdirection-e.md)模式下为导航点距离Swiper组件右边的距离，在 [LTR](../../apis-arkui/arkts-apis/arkts-arkui-layoutdirection-e.md)模式下为导航点距离Swiper组件左边的距离。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Indicator-start(value: LengthMetrics | undefined): this--><!--Device-Indicator-start(value: LengthMetrics | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [LengthMetrics](../../apis-arkui/arkts-apis/arkts-arkui-lengthmetrics-t.md) \| undefined | 是 | 设置在RTL模式下为导航点距离Swiper组件右边的距离，在LTR模式下为导航点距离Swiper组件左边的距离。<br/>默认值：0&lt;br/ &gt;单位：vp<br/>取值范围：[0, Swiper宽度-导航点区域宽度]，超出该范围时，取最近的边界值。<br/>取值为undefined时，按默认值处理。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## top

```TypeScript
top(value: Length | undefined): this
```

导航点顶部相对于Swiper的位置。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Indicator-top(value: Length | undefined): this--><!--Device-Indicator-top(value: Length | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../../apis-arkui/arkts-apis/arkts-arkui-length-t.md) \| undefined | 是 | 设置导航点顶部相对于Swiper的位置。<br/>未设置top和bottom时，进行自适应大小布局，按照指示器本身大小和Swiper的大小，在交叉轴方向上 ，位于底部，效果与设置bottom=0一致。<br/>设置为0时：按照0位置布局计算。<br/>优先级：高于bottom属性。<br/>取值范围：[0,Swiper高度-导航点区域高度]，超出该范围时，取最近的边界值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

