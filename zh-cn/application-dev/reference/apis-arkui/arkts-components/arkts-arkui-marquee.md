# Marquee

跑马灯组件，用于滚动展示一段单行文本。仅当文本内容宽度大于等于跑马灯组件宽度时滚动，当文本内容宽度小于跑马灯组件宽度时不滚动。

> **说明：**

> 为了不影响滚动帧率，建议在滚动类组件中Marquee的个数不超过4个，或者使用[Text]{@link text}组件的[TextOverflow.MARQUEE]{@link TextOverflow}替代。
>
> 对于Marquee组件动态帧率的场景，可以使用[MarqueeDynamicSyncScene]{@link @ohos.arkui.UIContext}接口实现。
>
> 在文本宽度小于跑马灯组件宽度时，使用[属性动画]{@link common}实现滚动。


## Marquee

```TypeScript
Marquee(options: MarqueeOptions)
```

创建跑马灯组件。

**起始版本：** 8

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | MarqueeOptions | 是 | 配置跑马灯组件的参数。 |

## 汇总

- [MarqueeOptions](arkts-arkui-marquee-marqueeoptions-i.md)
