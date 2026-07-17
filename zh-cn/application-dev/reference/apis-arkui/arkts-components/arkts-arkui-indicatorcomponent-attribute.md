# IndicatorComponent属性/事件

除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下属性。

**继承/实现关系：** IndicatorComponentAttribute extends [CommonMethod<IndicatorComponentAttribute>](CommonMethod<IndicatorComponentAttribute>)

**起始版本：** 15

<!--Device-unnamed-declare class IndicatorComponentAttribute extends CommonMethod<IndicatorComponentAttribute>--><!--Device-unnamed-declare class IndicatorComponentAttribute extends CommonMethod<IndicatorComponentAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## count

```TypeScript
count(totalCount: number)
```

设置导航点总数量。

单独导航点组件和Swiper绑定的时候，以Swiper的页面数量为准。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本15开始，该接口支持在ArkTS卡片中使用。

<!--Device-IndicatorComponentAttribute-count(totalCount: number): IndicatorComponentAttribute--><!--Device-IndicatorComponentAttribute-count(totalCount: number): IndicatorComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| totalCount | number | 是 |  |

## initialIndex

```TypeScript
initialIndex(index: number)
```

设置首次显示时当前导航点的索引值。设置小于0或大于等于导航点数量时，按照默认值0处理。

单独导航点组件和Swiper绑定的时候，该属性不生效。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本15开始，该接口支持在ArkTS卡片中使用。

<!--Device-IndicatorComponentAttribute-initialIndex(index: number): IndicatorComponentAttribute--><!--Device-IndicatorComponentAttribute-initialIndex(index: number): IndicatorComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 |  |

## loop

```TypeScript
loop(isLoop: boolean)
```

设置是否开启循环。

单独导航点组件和Swiper绑定的时候，该属性不生效。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本15开始，该接口支持在ArkTS卡片中使用。

<!--Device-IndicatorComponentAttribute-loop(isLoop: boolean): IndicatorComponentAttribute--><!--Device-IndicatorComponentAttribute-loop(isLoop: boolean): IndicatorComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isLoop | boolean | 是 |  |

## onChange

```TypeScript
onChange(event: Callback<number>)
```

Called when the index value changes.

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本15开始，该接口支持在ArkTS卡片中使用。

<!--Device-IndicatorComponentAttribute-onChange(event: Callback<number>): IndicatorComponentAttribute--><!--Device-IndicatorComponentAttribute-onChange(event: Callback<number>): IndicatorComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)<number> | 是 |  |

## style

```TypeScript
style(indicatorStyle: DotIndicator | DigitIndicator)
```

设置可选导航点指示器样式。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本15开始，该接口支持在ArkTS卡片中使用。

<!--Device-IndicatorComponentAttribute-style(indicatorStyle: DotIndicator | DigitIndicator): IndicatorComponentAttribute--><!--Device-IndicatorComponentAttribute-style(indicatorStyle: DotIndicator | DigitIndicator): IndicatorComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| indicatorStyle | DotIndicator \| DigitIndicator | 是 | 可选导航点指示器样式。<br/> - DotIndicator：圆点指示器样式。<br/> -DigitIndicator：数字指示器样式。<br/>  默认类型：DotIndicator。 |

## vertical

```TypeScript
vertical(isVertical: boolean)
```

设置是否为纵向滑动。

单独导航点组件和Swiper绑定的时候，该属性不生效。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本15开始，该接口支持在ArkTS卡片中使用。

<!--Device-IndicatorComponentAttribute-vertical(isVertical: boolean): IndicatorComponentAttribute--><!--Device-IndicatorComponentAttribute-vertical(isVertical: boolean): IndicatorComponentAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isVertical | boolean | 是 |  |

