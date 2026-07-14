# Rating

提供在给定范围内选择评分的组件。

> **说明：**

> - 当Rating的父节点有指定宽高时，需为Rating组件指定宽高，或为父节点设置值为true的[clip]{@link CommonMethod#clip(clip: Optional<boolean>)}属性。


## Rating

```TypeScript
Rating(options?: RatingOptions)
```

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | RatingOptions | 否 | 设置评分组件。<br/> 未设置时，则按照RatingOptions中各参数的默认值配置。 |

## 汇总

- [RatingConfiguration](arkts-arkui-rating-ratingconfiguration-i.md)
- [RatingOptions](arkts-arkui-rating-ratingoptions-i.md)
- [StarStyleOptions](arkts-arkui-rating-starstyleoptions-i.md)
- [OnRatingChangeCallback](arkts-arkui-rating-onratingchangecallback-t.md)
