# DataPanel属性/事件

除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下属性：

**继承/实现关系：** DataPanelAttribute extends [CommonMethod<DataPanelAttribute>]

**起始版本：** 7

<!--Device-unnamed-declare class DataPanelAttribute extends CommonMethod<DataPanelAttribute>--><!--Device-unnamed-declare class DataPanelAttribute extends CommonMethod<DataPanelAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## closeEffect

```TypeScript
closeEffect(value: boolean)
```

设置是否关闭数据占比图表旋转动效和投影效果。若未设置[trackShadow](DataPanelAttribute#trackShadow)属性，则由该属性控制投影效果的开关，开启投影的效果为投影的默认效果。若设置了trackShadow属性，则由trackShadow属性值控制投影效果的开关。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-DataPanelAttribute-closeEffect(value: boolean): DataPanelAttribute--><!--Device-DataPanelAttribute-closeEffect(value: boolean): DataPanelAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 关闭数据占比图表旋转动效和投影效果。<br/>默认值：false，false表示开启数据占比图表旋转动效和投影效果，true表示关闭数据占比图表旋转动效和投影效果。 |

## contentModifier

```TypeScript
contentModifier(modifier: ContentModifier<DataPanelConfiguration>)
```

定制DataPanel内容区的方法。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-DataPanelAttribute-contentModifier(modifier: ContentModifier<DataPanelConfiguration>): DataPanelAttribute--><!--Device-DataPanelAttribute-contentModifier(modifier: ContentModifier<DataPanelConfiguration>): DataPanelAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [ContentModifier](arkts-arkui-contentmodifier-i.md)&lt;DataPanelConfiguration&gt; | 是 | 在DataPanel组件上，定制内容区的方法。<br/>modifier：内容修改器，开发者需要自定义class实现ContentModifier接口。 |

## strokeWidth

```TypeScript
strokeWidth(value: Length)
```

设置圆环粗细。数据面板的类型为DataPanelType.Line时该属性不生效。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DataPanelAttribute-strokeWidth(value: Length): DataPanelAttribute--><!--Device-DataPanelAttribute-strokeWidth(value: Length): DataPanelAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | 是 | 圆环粗细。<br/>默认值：24<br/>单位：vp<br/>设置字符串类型参数时，如果不指定单位，默认单位为px，例如'10'，等同于'10px'。<br/>**说明：**<br/>设置小于0的值时，按默认值显示。<br/>请合理设置圆环粗细，当value大于圆环半径时，圆环粗细会自动设置为圆环半径的12%。如果value过大，圆环可能会消失。 |

## trackBackgroundColor

```TypeScript
trackBackgroundColor(value: ResourceColor)
```

设置底板颜色。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DataPanelAttribute-trackBackgroundColor(value: ResourceColor): DataPanelAttribute--><!--Device-DataPanelAttribute-trackBackgroundColor(value: ResourceColor): DataPanelAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 底板颜色。<br/>默认值：'#08182431'，格式为十六进制ARGB值，前两位代表透明度。 |

## trackShadow

```TypeScript
trackShadow(value: DataPanelShadowOptions)
```

设置投影样式。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DataPanelAttribute-trackShadow(value: DataPanelShadowOptions): DataPanelAttribute--><!--Device-DataPanelAttribute-trackShadow(value: DataPanelShadowOptions): DataPanelAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [DataPanelShadowOptions](arkts-arkui-datapanelshadowoptions-i.md) | 是 | 投影样式。<br/>**说明：** <br/>设置为null时，不开启投影。 |

## valueColors

```TypeScript
valueColors(value: Array<ResourceColor | LinearGradient>)
```

设置各数据段颜色。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-DataPanelAttribute-valueColors(value: Array<ResourceColor | LinearGradient>): DataPanelAttribute--><!--Device-DataPanelAttribute-valueColors(value: Array<ResourceColor | LinearGradient>): DataPanelAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Array&lt;ResourceColor \| LinearGradient&gt; | 是 | 各数据段颜色，ResourceColor为纯色，LinearGradient为渐变色。默认渐变色，其九段数据段默认颜色：[{ color: '#F7CE00', offset: 0 }, { color: '#F99B11', offset: 1 }]、[{ color: '#F76223', offset: 0 }, { color: '#F2400A', offset: 1 }]、[{ color: '#F772AC', offset: 0 }, { color: '#E65392', offset: 1 }]、[{ color: '#A575EB', offset: 0 }, { color: '#A12DF7', offset: 1 }]、[{ color: '#7B79F7', offset: 0 }, { color: '#4B48F7', offset: 1 }]、[{ color: '#4B8AF3', offset: 0 }, { color: '#007DFF', offset: 1 }]、[{ color: '#73C1E6', offset: 0 }, { color: '#4FB4E3', offset: 1 }]、[{ color: '#A5D61D', offset: 0 }, { color: '#69D14F', offset: 1 }]、[{ color: '#A2A2B0', offset: 0 }, { color: '#8E8E93', offset: 1 }] |

