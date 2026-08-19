# Rating

提供在给定范围内选择评分的组件，通常用于商品评价、内容打分等应用场景。 > **说明：** > - 当Rating的父节点有指定宽高时，需为Rating组件指定宽高，或为父节点设置值为true的clip属性。

## 子组件 无 ###### 键盘走焦规格 | 按键         | 功能描述                        | |------------|-----------------------------| | Tab        | 组件间切换焦点。                    | | 左右方向键   | 评分预览增加/减少（步长为stepSize），不改变实际分值。 | | Home       | 移动到第一个星星， 不改变实际分值。          | | End        | 移动到最后一个星星， 不改变实际分值。         | | Space/Enter | 将当前预览的评分值设置为实际评分。      |

## Rating

```TypeScript
Rating(options?: RatingOptions)
```

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-RatingInterface-(options?: RatingOptions): RatingAttribute--><!--Device-RatingInterface-(options?: RatingOptions): RatingAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [RatingOptions](arkts-arkui-ratingoptions-i.md) | 否 | 设置评分组件。<br/> 未设置时，则按照RatingOptions中各参数的默认值配置。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [RatingConfiguration](arkts-arkui-ratingconfiguration-i.md) | 开发者需要自定义class实现ContentModifier接口。继承自CommonConfiguration。 |
| [RatingOptions](arkts-arkui-ratingoptions-i.md) | 评分组件的信息。 @since版本号高于内层元素版本号的情况，但这不影响接口的使用。 |
| [StarStyleOptions](arkts-arkui-starstyleoptions-i.md) | 评分组件选中、未选中以及部分选中的星级样式。 @since版本号高于内层元素版本号的情况，但这不影响接口的使用。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [OnRatingChangeCallback](arkts-arkui-onratingchangecallback-t.md) | 当评分条的评分变化时触发该回调。 |

