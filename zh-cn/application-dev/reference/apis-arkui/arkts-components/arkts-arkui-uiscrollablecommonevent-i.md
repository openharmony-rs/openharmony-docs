# UIScrollableCommonEvent

Defines a UIScrollableCommonEvent which is used to set event to target component.

**继承/实现关系：** UIScrollableCommonEvent extends [UICommonEvent](arkts-arkui-uicommonevent-i.md)

**起始版本：** 19

<!--Device-unnamed-declare interface UIScrollableCommonEvent extends UICommonEvent--><!--Device-unnamed-declare interface UIScrollableCommonEvent extends UICommonEvent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="setonreachend"></a>
## setOnReachEnd

```TypeScript
setOnReachEnd(callback: Callback<void> | undefined): void
```

Set or reset the callback which is triggered when the scrolling reaches the end position.

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-UIScrollableCommonEvent-setOnReachEnd(callback: Callback<void> | undefined): void--><!--Device-UIScrollableCommonEvent-setOnReachEnd(callback: Callback<void> | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; \| undefined | 是 | callback function, triggered when the scrolling reaches the end position. |

<a id="setonreachstart"></a>
## setOnReachStart

```TypeScript
setOnReachStart(callback: Callback<void> | undefined): void
```

Set or reset the callback which is triggered when the scrolling reaches the start position.

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-UIScrollableCommonEvent-setOnReachStart(callback: Callback<void> | undefined): void--><!--Device-UIScrollableCommonEvent-setOnReachStart(callback: Callback<void> | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; \| undefined | 是 | callback function, triggered when the scrolling reaches the start position. |

<a id="setonscrollframebegin"></a>
## setOnScrollFrameBegin

```TypeScript
setOnScrollFrameBegin(callback: OnScrollFrameBeginCallback | undefined): void
```

Set or reset the callback which is triggered when scrolling begin each frame.

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-UIScrollableCommonEvent-setOnScrollFrameBegin(callback: OnScrollFrameBeginCallback | undefined): void--><!--Device-UIScrollableCommonEvent-setOnScrollFrameBegin(callback: OnScrollFrameBeginCallback | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnScrollFrameBeginCallback](arkts-arkui-onscrollframebegincallback-t.md) \| undefined | 是 | callback function, triggered when the scrolling begin each frame. |

<a id="setonscrollstart"></a>
## setOnScrollStart

```TypeScript
setOnScrollStart(callback: Callback<void> | undefined): void
```

Set or reset the callback which is triggered when the scrolling started.

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-UIScrollableCommonEvent-setOnScrollStart(callback: Callback<void> | undefined): void--><!--Device-UIScrollableCommonEvent-setOnScrollStart(callback: Callback<void> | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; \| undefined | 是 | callback function, triggered when the scrolling started. |

<a id="setonscrollstop"></a>
## setOnScrollStop

```TypeScript
setOnScrollStop(callback: Callback<void> | undefined): void
```

Set or reset the callback which is triggered when the scrolling stoped.

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-UIScrollableCommonEvent-setOnScrollStop(callback: Callback<void> | undefined): void--><!--Device-UIScrollableCommonEvent-setOnScrollStop(callback: Callback<void> | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; \| undefined | 是 | callback function, triggered when the scrolling stoped. |

