# IndicatorComponent属性/事件

除支持通用属性外，还支持以下属性。@extends CommonMethod&lt;IndicatorComponentAttribute&gt;

**继承/实现关系：** IndicatorComponentAttribute extends CommonMethod<IndicatorComponentAttribute>

**起始版本：** 15

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## count

```TypeScript
count(totalCount: number)
```

设置导航点总数量。单独导航点组件和Swiper绑定的时候，以Swiper的页面数量为准。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本15开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| totalCount | number | 是 |  |

## initialIndex

```TypeScript
initialIndex(index: number)
```

设置首次显示时当前导航点的索引值。传入值小于0或大于等于导航点数量时，按照默认值0处理。单独导航点组件和Swiper绑定的时候，该属性不生效。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本15开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | number | 是 |  |

## loop

```TypeScript
loop(isLoop: boolean)
```

设置是否开启循环。单独导航点组件和Swiper绑定的时候，该属性不生效。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本15开始，该接口支持在ArkTS卡片中使用。

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

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | Callback & lt;number & gt; | 是 |  |

## style

```TypeScript
style(indicatorStyle: DotIndicator | DigitIndicator)
```

设置可选导航点指示器样式。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本15开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| indicatorStyle | [DotIndicator](arkts-arkui-dotindicator-c.md) \| [DigitIndicator](arkts-arkui-digitindicator-c.md) | 是 | 可选导航点指示器样式。    - DotIndicator：圆点指示器样式。    - DigitIndicator：数字指示器样式。     默认类型：DotIndicator。 |

## vertical

```TypeScript
vertical(isVertical: boolean)
```

设置是否为纵向滑动。单独导航点组件和Swiper绑定的时候，该属性不生效。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本15开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isVertical | boolean | 是 |  |
