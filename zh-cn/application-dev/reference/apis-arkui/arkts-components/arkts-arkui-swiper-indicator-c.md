# Indicator

设置导航点距离Swiper组件距离。由于导航点有默认交互区域，交互区域高度为32vp，所以无法让显示部分完全贴底。若想实现完全贴底，可以使用[IndicatorComponent](../../../../reference/apis-arkui/arkui-ts/ts-swiper-components-indicator.md#indicatorcomponent)组件，更灵活地调整位置。

**起始版本：** 10

<!--Device-unnamed-declare class Indicator<T>--><!--Device-unnamed-declare class Indicator<T>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## bottom

```TypeScript
bottom(value: Length): T
```

导航点底部相对于Swiper的位置。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-Indicator-bottom(value: Length): T--><!--Device-Indicator-bottom(value: Length): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | 是 | 设置导航点底部相对于Swiper的位置。<br/>未设置top和bottom时，进行自适应大小布局，按照指示器本身大小和Swiper的大小，在交叉轴方向上，位于底部，效果与设置bottom=0一致。<br/>设置为0时：按照0位置布局计算。<br/>优先级：低于top属性。<br/>取值范围：[0,Swiper高度-导航点区域高度]，超出该范围时，取最近的边界值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前导航点指示器。 |

## bottom

```TypeScript
bottom(bottom: LengthMetrics | Length, ignoreSize: boolean): T
```

导航点底部相对于Swiper的位置，并可通过ignoreSize属性忽略导航点大小。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本19开始，该接口支持在ArkTS卡片中使用。

<!--Device-Indicator-bottom(bottom: LengthMetrics | Length, ignoreSize: boolean): T--><!--Device-Indicator-bottom(bottom: LengthMetrics | Length, ignoreSize: boolean): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| bottom | LengthMetrics \| Length | 是 | 设置导航点底部相对于Swiper的位置。<br/>未设置top和bottom时，进行自适应大小布局，按照指示器本身大小和Swiper的大小，在交叉轴方向上，位于底部，效果与设置bottom=0一致。<br/>设置为0时：按照0位置布局计算。<br/>优先级：低于top属性。<br/>取值范围：[0,Swiper高度-导航点区域高度]，超出该范围时，取最近的边界值。 |
| ignoreSize | boolean | 是 | 设置是否忽略导航点本身大小，默认false。<br/>设为true时可以将导航点更靠近Swiper底部，使用方法可以参考[示例9演示导航点space与bottom](../../../../reference/apis-arkui/arkui-ts/ts-container-swiper.md#示例9演示导航点space与bottom)。<br/> 说明：[数字导航点](arkts-arkui-swiper-digitindicator-c.md)ignoreSize属性，不生效的场景如下：<br/> • 当[vertical](SwiperAttribute#vertical) 设置为false，且bottom &gt; 0。<br/> • 当[vertical](SwiperAttribute#vertical) 设置为true时：<br/>1、bottom &gt; 0 时。<br/> 2、bottom设为undefined。 <br/> 3、isSidebarMiddle设置为false时。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前导航点指示器。 |

## digit

```TypeScript
static digit(): DigitIndicator
```

返回一个DigitIndicator对象。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-Indicator-static digit(): DigitIndicator--><!--Device-Indicator-static digit(): DigitIndicator-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DigitIndicator](arkts-arkui-swiper-digitindicator-c.md) | 数字指示器。 |

## dot

```TypeScript
static dot(): DotIndicator
```

返回一个DotIndicator对象。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-Indicator-static dot(): DotIndicator--><!--Device-Indicator-static dot(): DotIndicator-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DotIndicator](arkts-arkui-swiper-dotindicator-c.md) | 圆点指示器。 |

## end

```TypeScript
end(value: LengthMetrics): T
```

在RTL模式下为导航点距离Swiper组件左边的距离，在LTR模式下为导航点距离Swiper组件右边的距离。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-Indicator-end(value: LengthMetrics): T--><!--Device-Indicator-end(value: LengthMetrics): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [LengthMetrics](../arkts-apis/arkts-arkui-lengthmetrics-t.md) | 是 | 设置在RTL模式下为导航点距离Swiper组件左边的距离，在LTR模式下为导航点距离Swiper组件右边的距离。<br/>默认值：0<br/>单位：vp<br/>取值范围：[0, Swiper宽度-导航点区域宽度]，超出该范围时，取最近的边界值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前导航点指示器。 |

## left

```TypeScript
left(value: Length): T
```

导航点左侧相对于Swiper的位置。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-Indicator-left(value: Length): T--><!--Device-Indicator-left(value: Length): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | 是 | 设置导航点左侧相对于Swiper的位置。<br/>未设置left和right时，进行自适应大小布局，按照指示器本身大小和Swiper的大小在主轴方向上进行居中对齐。<br/>设置为0时：按照0位置布局计算。<br/>优先级：高于right属性。<br/>取值范围：[0,Swiper宽度-导航点区域宽度]，超出该范围时，取最近的边界值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前导航点指示器。 |

## right

```TypeScript
right(value: Length): T
```

导航点右侧相对于Swiper的位置。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-Indicator-right(value: Length): T--><!--Device-Indicator-right(value: Length): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | 是 | 设置导航点右侧相对于Swiper的位置。<br/>未设置left和right时，进行自适应大小布局，按照指示器本身大小和Swiper的大小在主轴方向上进行居中对齐。<br/>设置为0时：按照0位置布局计算。<br/>优先级：低于left属性。<br/>取值范围：[0,Swiper宽度-导航点区域宽度]，超出该范围 时，取最近的边界值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前导航点指示器。 |

## start

```TypeScript
start(value: LengthMetrics): T
```

在[RTL](../arkts-apis/arkts-arkui-state-management-layoutdirection-e.md)模式下为导航点距离Swiper组件右边的距离，在[LTR](../arkts-apis/arkts-arkui-state-management-layoutdirection-e.md)模式下为导航点距离Swiper组件左边的距离。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-Indicator-start(value: LengthMetrics): T--><!--Device-Indicator-start(value: LengthMetrics): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [LengthMetrics](../arkts-apis/arkts-arkui-lengthmetrics-t.md) | 是 | 设置在RTL模式下为导航点距离Swiper组件右边的距离，在LTR模式下为导航点距离Swiper组件左边的距离。<br/>默认值：0<br/>单位：vp<br/>取值范围：[0, Swiper宽度-导航点区域宽度]，超出该范围时，取最近的边界值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前导航点指示器。 |

## top

```TypeScript
top(value: Length): T
```

导航点顶部相对于Swiper的位置。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-Indicator-top(value: Length): T--><!--Device-Indicator-top(value: Length): T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | 是 | 设置导航点顶部相对于Swiper的位置。<br/>未设置top和bottom时，进行自适应大小布局，按照指示器本身大小和Swiper的大小，在交叉轴方向上，位于底部，效果与设置bottom=0一致。<br/>设置为0时：按照0位置布局计算。<br/>优先级：高于bottom属性。<br/>取值范围：[0,Swiper高度-导航点区域高度]，超出该范围时，取最近的边界值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 返回当前导航点指示器。 |

