# IndicatorComponentAttribute

除支持[通用属性]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_外，还支持以下属性。

**继承/实现关系：** IndicatorComponentAttribute extends [CommonMethod](../../../apis-na/arkts-apis/arkts-na-component/common-commonmethod-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface IndicatorComponentAttribute extends CommonMethod--><!--Device-unnamed-export declare interface IndicatorComponentAttribute extends CommonMethod-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## count

```TypeScript
count(totalCount: int | undefined): this
```

设置导航点总数量。 单独导航点组件和Swiper绑定的时候，以Swiper的页面数量为准。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IndicatorComponentAttribute-count(totalCount: int | undefined): this--><!--Device-IndicatorComponentAttribute-count(totalCount: int | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| totalCount | int \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## initialIndex

```TypeScript
initialIndex(index: int | undefined): this
```

设置首次显示时当前导航点的索引值。设置小于0或大于等于导航点数量时，按照默认值0处理。 单独导航点组件和Swiper绑定的时候，该属性不生效。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IndicatorComponentAttribute-initialIndex(index: int | undefined): this--><!--Device-IndicatorComponentAttribute-initialIndex(index: int | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## loop

```TypeScript
loop(isLoop: boolean | undefined): this
```

设置是否开启循环。 单独导航点组件和Swiper绑定的时候，该属性不生效。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IndicatorComponentAttribute-loop(isLoop: boolean | undefined): this--><!--Device-IndicatorComponentAttribute-loop(isLoop: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isLoop | boolean \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## onChange

```TypeScript
onChange(event: Callback<int> | undefined): this
```

当前显示的选中导航点索引变化时触发该事件，可通过回调函数获取当前选中导航点的索引值。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IndicatorComponentAttribute-onChange(event: Callback<int> | undefined): this--><!--Device-IndicatorComponentAttribute-onChange(event: Callback<int> | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;int&gt; \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## setIndicatorComponentOptions

```TypeScript
default setIndicatorComponentOptions(controller?: IndicatorComponentController): this
```

设置indicatorComponent组件配置项。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IndicatorComponentAttribute-default setIndicatorComponentOptions(controller?: IndicatorComponentController): this--><!--Device-IndicatorComponentAttribute-default setIndicatorComponentOptions(controller?: IndicatorComponentController): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| controller | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | IndicatorComponent构造函数选项 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this | 返回IndicatorComponentAttribute的实例。 |

## style

```TypeScript
style(indicatorStyle: DotIndicator | DigitIndicator | undefined): this
```

设置可选导航点指示器样式。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IndicatorComponentAttribute-style(indicatorStyle: DotIndicator | DigitIndicator | undefined): this--><!--Device-IndicatorComponentAttribute-style(indicatorStyle: DotIndicator | DigitIndicator | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| indicatorStyle | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| DigitIndicator \| undefined | 是 | 可选导航点指示器样式。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ - DotIndicator：圆点指示器样式。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_   - DigitIndicator：数字指示器样式。\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_2\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_  默认类型：DotIndicator。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

## vertical

```TypeScript
vertical(isVertical: boolean | undefined): this
```

设置是否为纵向滑动。 单独导航点组件和Swiper绑定的时候，该属性不生效。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-IndicatorComponentAttribute-vertical(isVertical: boolean | undefined): this--><!--Device-IndicatorComponentAttribute-vertical(isVertical: boolean | undefined): this-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isVertical | boolean \| undefined | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| this |  |

