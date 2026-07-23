# Marquee属性/事件

除支持[通用属性](../../apis-ability-kit/arkts-apis/arkts-app-ability-common.md)外，还支持以下属性：

**继承/实现关系：** MarqueeAttribute extends [CommonMethod<MarqueeAttribute>]

**起始版本：** 8

<!--Device-unnamed-declare class MarqueeAttribute extends CommonMethod<MarqueeAttribute>--><!--Device-unnamed-declare class MarqueeAttribute extends CommonMethod<MarqueeAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## allowScale

```TypeScript
allowScale(value: boolean)
```

设置是否允许文本缩放。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-MarqueeAttribute-allowScale(value: boolean): MarqueeAttribute--><!--Device-MarqueeAttribute-allowScale(value: boolean): MarqueeAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | boolean | 是 | 是否允许文本缩放。<br/>true：允许文本缩放；false：不允许文本缩放。<br/>默认值：false<br/>**说明：**<br/>仅当[fontSize](MarqueeAttribute#fontSize)为fp单位时生效。 |

## fontColor

```TypeScript
fontColor(value: ResourceColor)
```

设置字体颜色。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-MarqueeAttribute-fontColor(value: ResourceColor): MarqueeAttribute--><!--Device-MarqueeAttribute-fontColor(value: ResourceColor): MarqueeAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 字体颜色。<br />Wearable设备上默认值为：'#c5ffffff'，显示为淡蓝色，其他设备默认值为：'e6182431'，显示为黑色。 |

## fontFamily

```TypeScript
fontFamily(value: string | Resource)
```

设置字体列表。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-MarqueeAttribute-fontFamily(value: string | Resource): MarqueeAttribute--><!--Device-MarqueeAttribute-fontFamily(value: string | Resource): MarqueeAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string \| Resource | 是 | 字体列表。默认字体'HarmonyOS Sans'。<br>应用当前支持'HarmonyOS Sans'字体和注册自定义字体[loadFontSync](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-fontcollection-c.md#loadfontsync)。<br>卡片当前仅支持'HarmonyOS Sans'字体。 |

## fontSize

```TypeScript
fontSize(value: Length)
```

设置字体大小。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-MarqueeAttribute-fontSize(value: Length): MarqueeAttribute--><!--Device-MarqueeAttribute-fontSize(value: Length): MarqueeAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | 是 | 字体大小。fontSize为number类型时，使用fp单位。字体默认大小16fp。不支持设置百分比字符串。 |

## fontWeight

```TypeScript
fontWeight(value: number | FontWeight | string)
```

设置文本的字体粗细，设置过大可能会在不同字体下有截断。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-MarqueeAttribute-fontWeight(value: number | FontWeight | string): MarqueeAttribute--><!--Device-MarqueeAttribute-fontWeight(value: number | FontWeight | string): MarqueeAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| FontWeight \| string | 是 | 文本的字体粗细，number类型取值[100, 900]，取值间隔为100，默认为400，取值越大，字体越粗。string类型仅支持number类型取值的字符串形式，例如"400"，以及"bold"、"bolder"、"lighter"、"regular"、"medium"，分别对应FontWeight中相应的枚举值。<br/>默认值：FontWeight.Normal |

## marqueeUpdateStrategy

```TypeScript
marqueeUpdateStrategy(value: MarqueeUpdateStrategy)
```

跑马灯组件属性更新后，跑马灯的滚动策略。(当跑马灯为播放状态，且文本内容宽度超过跑马灯组件宽度时，该属性生效。)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-MarqueeAttribute-marqueeUpdateStrategy(value: MarqueeUpdateStrategy): MarqueeAttribute--><!--Device-MarqueeAttribute-marqueeUpdateStrategy(value: MarqueeUpdateStrategy): MarqueeAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [MarqueeUpdateStrategy](../arkts-apis/arkts-arkui-marqueeupdatestrategy-e.md) | 是 | 跑马灯组件属性更新后，跑马灯的滚动策略。<br/>默认值: MarqueeUpdateStrategy.DEFAULT |

## onBounce

```TypeScript
onBounce(event: () => void)
```

完成一次滚动时触发，若循环次数不为1，则该事件会多次触发。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-MarqueeAttribute-onBounce(event: () => void): MarqueeAttribute--><!--Device-MarqueeAttribute-onBounce(event: () => void): MarqueeAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | () =&gt; void | 是 | 完成一次滚动时触发的回调。 |

## onFinish

```TypeScript
onFinish(event: () => void)
```

滚动全部循环次数完成时触发回调。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-MarqueeAttribute-onFinish(event: () => void): MarqueeAttribute--><!--Device-MarqueeAttribute-onFinish(event: () => void): MarqueeAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | () =&gt; void | 是 | 滚动全部循环次数完成时的回调。 |

## onStart

```TypeScript
onStart(event: () => void)
```

当滚动的文本内容变化或者开始滚动时触发回调。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-MarqueeAttribute-onStart(event: () => void): MarqueeAttribute--><!--Device-MarqueeAttribute-onStart(event: () => void): MarqueeAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | () =&gt; void | 是 | 当滚动的文本内容变化或者开始滚动时的回调。 |

## onStop

```TypeScript
onStop(event: Callback<void> | undefined)
```

跑马灯滚动结束或停止时触发回调。

跑马灯停止表示跑马灯将从开始位置，重新开始循环，不包含暂停场景，暂停不会触发该回调。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-MarqueeAttribute-onStop(event: Callback<void> | undefined): MarqueeAttribute--><!--Device-MarqueeAttribute-onStop(event: Callback<void> | undefined): MarqueeAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; \| undefined | 是 |  |

