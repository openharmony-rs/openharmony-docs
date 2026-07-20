# UIWaterFlowEvent

frameNode中[getEvent('WaterFlow')](../arkts-apis/arkts-arkui-typenode-getevent-f.md#getevent-1)方法的返回值，可用于给WaterFlow节点设置滚动事件。

UIWaterFlowEvent继承于[UIScrollableCommonEvent](arkts-arkui-uiscrollablecommonevent-i.md)。

**继承/实现关系：** UIWaterFlowEvent extends [UIScrollableCommonEvent](arkts-arkui-uiscrollablecommonevent-i.md)

**起始版本：** 19

<!--Device-unnamed-declare interface UIWaterFlowEvent extends UIScrollableCommonEvent--><!--Device-unnamed-declare interface UIWaterFlowEvent extends UIScrollableCommonEvent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="setondidscroll"></a>
## setOnDidScroll

```TypeScript
setOnDidScroll(callback: OnScrollCallback | undefined): void
```

设置[onDidScroll](docroot://reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#ondidscroll12)事件的回调。

方法入参为undefined时，会重置事件回调。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-UIWaterFlowEvent-setOnDidScroll(callback: OnScrollCallback | undefined): void--><!--Device-UIWaterFlowEvent-setOnDidScroll(callback: OnScrollCallback | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnScrollCallback](arkts-arkui-onscrollcallback-t.md) \| undefined | 是 | onDidScroll事件的回调函数。 |

<a id="setonscrollindex"></a>
## setOnScrollIndex

```TypeScript
setOnScrollIndex(callback: OnWaterFlowScrollIndexCallback | undefined): void
```

设置[onScrollIndex](docroot://reference/apis-arkui/arkui-ts/ts-container-waterflow.md#onscrollindex11)事件的回调。

方法入参为undefined时，会重置事件回调。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-UIWaterFlowEvent-setOnScrollIndex(callback: OnWaterFlowScrollIndexCallback | undefined): void--><!--Device-UIWaterFlowEvent-setOnScrollIndex(callback: OnWaterFlowScrollIndexCallback | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnWaterFlowScrollIndexCallback](arkts-arkui-onwaterflowscrollindexcallback-t.md) \| undefined | 是 | onScrollIndex事件的回调函数。 |

<a id="setonwillscroll"></a>
## setOnWillScroll

```TypeScript
setOnWillScroll(callback: OnWillScrollCallback | undefined): void
```

设置[onWillScroll](docroot://reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#onwillscroll12)事件的回调。

方法入参为undefined时，会重置事件回调。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-UIWaterFlowEvent-setOnWillScroll(callback: OnWillScrollCallback | undefined): void--><!--Device-UIWaterFlowEvent-setOnWillScroll(callback: OnWillScrollCallback | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnWillScrollCallback](arkts-arkui-onwillscrollcallback-t.md) \| undefined | 是 | onWillScroll事件的回调函数。 |

