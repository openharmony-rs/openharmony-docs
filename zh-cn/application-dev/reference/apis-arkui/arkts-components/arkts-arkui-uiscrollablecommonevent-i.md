# UIScrollableCommonEvent

用于设置滚动事件回调。

**继承/实现关系：** UIScrollableCommonEvent extends [UICommonEvent](arkts-arkui-uicommonevent-i.md)

**起始版本：** 19

<!--Device-unnamed-declare interface UIScrollableCommonEvent--><!--Device-unnamed-declare interface UIScrollableCommonEvent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## setOnReachEnd

```TypeScript
setOnReachEnd(callback: Callback<void> | undefined): void
```

设置[onReachEnd](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#onreachend11)事件的回调。 方法入参为undefined时，会重置事件回调。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-UIScrollableCommonEvent-setOnReachEnd(callback: Callback<void> | undefined): void--><!--Device-UIScrollableCommonEvent-setOnReachEnd(callback: Callback<void> | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](arkts-arkui-callback-i.md)&lt;void&gt; \| undefined | 是 | onReachEnd事件的回调函数。 |

## setOnReachStart

```TypeScript
setOnReachStart(callback: Callback<void> | undefined): void
```

设置[onReachStart](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#onreachstart11)事件的回调。 方法入参为undefined时，会重置事件回调。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-UIScrollableCommonEvent-setOnReachStart(callback: Callback<void> | undefined): void--><!--Device-UIScrollableCommonEvent-setOnReachStart(callback: Callback<void> | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](arkts-arkui-callback-i.md)&lt;void&gt; \| undefined | 是 | onReachStart事件的回调函数。 |

## setOnScrollFrameBegin

```TypeScript
setOnScrollFrameBegin(callback: OnScrollFrameBeginCallback | undefined): void
```

设置onScrollFrameBegin事件的回调。 方法入参为undefined时，会重置事件回调。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-UIScrollableCommonEvent-setOnScrollFrameBegin(callback: OnScrollFrameBeginCallback | undefined): void--><!--Device-UIScrollableCommonEvent-setOnScrollFrameBegin(callback: OnScrollFrameBeginCallback | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | OnScrollFrameBeginCallback \| undefined | 是 | onScrollFrameBegin事件的回调函数。 |

## setOnScrollStart

```TypeScript
setOnScrollStart(callback: Callback<void> | undefined): void
```

设置[onScrollStart](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#onscrollstart11)事件的回调。 方法入参为undefined时，会重置事件回调。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-UIScrollableCommonEvent-setOnScrollStart(callback: Callback<void> | undefined): void--><!--Device-UIScrollableCommonEvent-setOnScrollStart(callback: Callback<void> | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](arkts-arkui-callback-i.md)&lt;void&gt; \| undefined | 是 | onScrollStart事件的回调函数。 |

## setOnScrollStop

```TypeScript
setOnScrollStop(callback: Callback<void> | undefined): void
```

设置[onScrollStop](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#onscrollstop11)事件的回调。 方法入参为undefined时，会重置事件回调。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-UIScrollableCommonEvent-setOnScrollStop(callback: Callback<void> | undefined): void--><!--Device-UIScrollableCommonEvent-setOnScrollStop(callback: Callback<void> | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [Callback](arkts-arkui-callback-i.md)&lt;void&gt; \| undefined | 是 | onScrollStop事件的回调函数。 |

