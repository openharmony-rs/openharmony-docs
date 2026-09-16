# Rating

提供在给定范围内选择评分的组件，通常用于商品评价、内容打分等应用场景。

> **说明：**

> - 当Rating的父节点有指定宽高时，需为Rating组件指定宽高，或为父节点设置值为true的clip属性。

## 子组件

无

## 键盘走焦规格

| 按键 | 功能描述 |  
|------------|-----------------------------|  
| Tab | 组件间切换焦点。 |
| 左右方向键 | 评分预览增加/减少（步长为stepSize），不改变实际分值。 |
| Home | 移动到第一个星星， 不改变实际分值。 |
| End | 移动到最后一个星星， 不改变实际分值。 |
| Space/Enter | 将当前预览的评分值设置为实际评分。 |

## Rating

```TypeScript
Rating(options?: RatingOptions)
```

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [RatingOptions](arkts-arkui-ratingoptions-i.md) | 否 | 设置评分组件。<br> 未设置时，则按照RatingOptions中各参数的默认值配置。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [RatingConfiguration](arkts-arkui-ratingconfiguration-i.md) | 开发者需要自定义class实现ContentModifier接口。继承自[CommonConfiguration](arkts-arkui-commonconfiguration-i.md)。 |
| [RatingOptions](arkts-arkui-ratingoptions-i.md) | 评分组件的信息。 |
| [StarStyleOptions](arkts-arkui-starstyleoptions-i.md) | 评分组件选中、未选中以及部分选中的星级样式。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [OnRatingChangeCallback](arkts-arkui-onratingchangecallback-t.md) | 当评分条的评分变化时触发该回调。 |

## 示例

```TypeScript
### 示例1（设置默认评分样式）

以下示例展示了如何创建默认星型评分样式。


```

```TypeScript
### 示例2（自定义评分条）

以下示例实现自定义评分条，其中每个圆圈表示0.5分。ratingIndicator为true时，评分条作为指示器使用，不可改变评分。ratingStars用于设置评分总数，ratingStepSize用于设置评分步长。


```

```TypeScript
### 示例3（通过Resource资源设置评分的样式）

该示例通过Resource资源配置starStyle，实现自定义星级图片链接，API version 20之后推荐使用该方法设置样式。


```

```TypeScript
### 示例4（设置评分的样式）

以下示例展示了如何通过配置starStyle实现自定义星级的图片链接。

> 说明
> 
> 此示例的资源不在src > main > resource目录下，从DevEco Studio 6.0.0 Beta2开始，新建工程或者模块时，默认创建的模块不会对非resources目录下的资源进行打包，需使能相关开关：模块的build-profile.json5中buildOptions > resOptions > copyCodeResource > enable设置为true，详见[resOptions](https://developer.huawei.com/consumer/cn/doc/harmonyos-guides/ide-hvigor-build-profile#section754823013348)中相关介绍。
```
