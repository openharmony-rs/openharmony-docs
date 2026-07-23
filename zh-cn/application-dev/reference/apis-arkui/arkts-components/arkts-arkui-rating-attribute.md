# Rating属性/事件

**继承/实现关系：** RatingAttribute extends [CommonMethod<RatingAttribute>]

**起始版本：** 7

<!--Device-unnamed-declare class RatingAttribute extends CommonMethod<RatingAttribute>--><!--Device-unnamed-declare class RatingAttribute extends CommonMethod<RatingAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## contentModifier

```TypeScript
contentModifier(modifier: ContentModifier<RatingConfiguration>)
```

定制Rating内容区的方法。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RatingAttribute-contentModifier(modifier: ContentModifier<RatingConfiguration>): RatingAttribute--><!--Device-RatingAttribute-contentModifier(modifier: ContentModifier<RatingConfiguration>): RatingAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [ContentModifier](arkts-arkui-contentmodifier-i.md)&lt;RatingConfiguration&gt; | 是 | 在Rating组件上，定制内容区的方法。<br/>modifier：内容修改器，开发者需要自定义class实现ContentModifier接口。 |

## contentModifier

```TypeScript
contentModifier(modifier: Optional<ContentModifier<RatingConfiguration>>)
```

定制Rating内容区的方法。与[contentModifier](RatingAttribute#contentModifier(modifier: ContentModifier<RatingConfiguration>))相比，modifier参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-RatingAttribute-contentModifier(modifier: Optional<ContentModifier<RatingConfiguration>>): RatingAttribute--><!--Device-RatingAttribute-contentModifier(modifier: Optional<ContentModifier<RatingConfiguration>>): RatingAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [Optional](arkts-arkui-optional-t.md)&lt;ContentModifier&lt;RatingConfiguration&gt;&gt; | 是 | 在Rating组件上，定制内容区的方法。<br/>modifier：内容修改器，开发者需要自定义class实现ContentModifier接口。<br/>当modifier的值为undefined时，不使用内容修改器。 |

## onChange

```TypeScript
onChange(callback: (value: number) => void)
```

当评分条的评星变化时触发该回调。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-RatingAttribute-onChange(callback: (value: number) => void): RatingAttribute--><!--Device-RatingAttribute-onChange(callback: (value: number) => void): RatingAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | (value: number) =&gt; void | 是 |  |

## onChange

```TypeScript
onChange(callback: Optional<OnRatingChangeCallback>)
```

当评分条的评星变化时触发该回调。与[onChange](RatingAttribute#onChange(callback: (value: number) => void))相比，callback参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-RatingAttribute-onChange(callback: Optional<OnRatingChangeCallback>): RatingAttribute--><!--Device-RatingAttribute-onChange(callback: Optional<OnRatingChangeCallback>): RatingAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Optional](arkts-arkui-optional-t.md)&lt;OnRatingChangeCallback&gt; | 是 | 操作评分条的评星变化时触发该回调。<br/>当callback的值为undefined时，不使用回调函数。 |

## starStyle

```TypeScript
starStyle(options: StarStyleOptions)
```

设置评分的样式。该属性所支持的图片类型能力参考[Image](../../apis-image-kit/arkts-apis/arkts-multimedia-image.md)组件。

支持加载本地图片和网络图片，暂不支持PixelMap类型。

默认图片加载方式为异步，暂不支持同步加载。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-RatingAttribute-starStyle(options: StarStyleOptions): RatingAttribute--><!--Device-RatingAttribute-starStyle(options: StarStyleOptions): RatingAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [StarStyleOptions](arkts-arkui-starstyleoptions-i.md) | 是 | 评分的样式。<br/>**说明：** <br/>当backgroundUri、foregroundUri或secondaryUri设置的图片路径错误时，图片将保持上次的图片显示结果。如果首次设置错误，则不显示图片。<br/>当backgroundUri或foregroundUri设置为undefined或空字符串时，Rating组件将加载系统默认星型图源。<br/>当secondaryUri未设置或设置为undefined或空字符串时，将优先使用backgroundUri，效果等同于仅设置foregroundUri和backgroundUri。<br>**起始版本：** 18 |

## starStyle

```TypeScript
starStyle(options: Optional<StarStyleOptions>)
```

设置评分的样式。该属性所支持的图片类型能力参考[Image](../../apis-image-kit/arkts-apis/arkts-multimedia-image.md)组件。

支持加载本地图片和网络图片，暂不支持PixelMap类型。

默认图片加载方式为异步，暂不支持同步加载。

与[starStyle](RatingAttribute#starStyle(options: StarStyleOptions))相比，options参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-RatingAttribute-starStyle(options: Optional<StarStyleOptions>): RatingAttribute--><!--Device-RatingAttribute-starStyle(options: Optional<StarStyleOptions>): RatingAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [Optional](arkts-arkui-optional-t.md)&lt;StarStyleOptions&gt; | 是 | 评分的样式。<br/>**说明：** <br/>当backgroundUri、foregroundUri或secondaryUri设置的图片路径错误时，图片将保持上次的图片显示结果。如果首次设置错误，则不显示图片。<br/>当backgroundUri或foregroundUri设置为undefined或空字符串时，Rating组件将加载系统默认星型图源。<br/>当secondaryUri未设置或设置为undefined或空字符串时，将优先使用backgroundUri，效果等同于仅设置foregroundUri和backgroundUri。 |

## stars

```TypeScript
stars(value: number)
```

设置评分总数。设置为小于等于0的值时，按默认值显示。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-RatingAttribute-stars(value: number): RatingAttribute--><!--Device-RatingAttribute-stars(value: number): RatingAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 设置评分总数。<br/>默认值：5 |

## stars

```TypeScript
stars(starCount: Optional<number>)
```

设置评分总数。设置为小于等于0的值时，按默认值显示。与[stars](RatingAttribute#stars(value: number))相比，starCount参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-RatingAttribute-stars(starCount: Optional<number>): RatingAttribute--><!--Device-RatingAttribute-stars(starCount: Optional<number>): RatingAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| starCount | [Optional](arkts-arkui-optional-t.md)&lt;number&gt; | 是 | 设置评分总数。<br/>当starCount的值为undefined时，默认值：5 |

## stepSize

```TypeScript
stepSize(value: number)
```

设置操作评级的步长。设置为小于0.1的值时，按默认值显示。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-RatingAttribute-stepSize(value: number): RatingAttribute--><!--Device-RatingAttribute-stepSize(value: number): RatingAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 操作评级的步长。<br/>默认值：0.5<br/>取值范围：[0.1, stars] |

## stepSize

```TypeScript
stepSize(size: Optional<number>)
```

设置操作评级的步长。设置为小于0.1的值时，按默认值显示。与[stepSize](RatingAttribute#stepSize(value: number))相比，size参数新增了对undefined类型的支持。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

<!--Device-RatingAttribute-stepSize(size: Optional<number>): RatingAttribute--><!--Device-RatingAttribute-stepSize(size: Optional<number>): RatingAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| size | [Optional](arkts-arkui-optional-t.md)&lt;number&gt; | 是 | 操作评级的步长。<br/>当size的值为undefined时，默认值：0.5<br/>取值范围：[0.1, stars] |

