# UIWaterFlowEvent

frameNode中 [getEvent('WaterFlow')](../arkts-apis/arkts-arkui-typenode-getevent-f.md)方法的返 回值，可用于给WaterFlow节点设置滚动事件。 UIWaterFlowEvent继承于UIScrollableCommonEvent。

**继承/实现关系：** UIWaterFlowEvent extends UIScrollableCommonEvent

**起始版本：** 19

<!--Device-unnamed-declare interface UIWaterFlowEvent--><!--Device-unnamed-declare interface UIWaterFlowEvent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## setOnDidScroll

```TypeScript
setOnDidScroll(callback: OnScrollCallback | undefined): void
```

设置[onDidScroll](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#ondidscroll12)事件的回调。 > **说明：** > > setOnWillScroll用于设置每帧滚动开始前的回调，setOnDidScroll用于设置每帧滚动完成后的回调。两者可同时使用，setOnWillScroll的回调先于setOnDidScroll触发。 > 方法入参为undefined时，会重置事件回调。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-UIWaterFlowEvent-setOnDidScroll(callback: OnScrollCallback | undefined): void--><!--Device-UIWaterFlowEvent-setOnDidScroll(callback: OnScrollCallback | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | OnScrollCallback \| undefined | 是 | onDidScroll事件的回调函数。 |

## setOnScrollIndex

```TypeScript
setOnScrollIndex(callback: OnWaterFlowScrollIndexCallback | undefined): void
```

设置onScrollIndex事件的回调。 方法入参为undefined时，会重置事件回调。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-UIWaterFlowEvent-setOnScrollIndex(callback: OnWaterFlowScrollIndexCallback | undefined): void--><!--Device-UIWaterFlowEvent-setOnScrollIndex(callback: OnWaterFlowScrollIndexCallback | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnWaterFlowScrollIndexCallback](arkts-arkui-onwaterflowscrollindexcallback-t.md) \| undefined | 是 | onScrollIndex事件的回调函数。 |

## setOnWillScroll

```TypeScript
setOnWillScroll(callback: OnWillScrollCallback | undefined): void
```

设置[onWillScroll](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#onwillscroll12)事件的回调。 方法入参为undefined时，会重置事件回调。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-UIWaterFlowEvent-setOnWillScroll(callback: OnWillScrollCallback | undefined): void--><!--Device-UIWaterFlowEvent-setOnWillScroll(callback: OnWillScrollCallback | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | OnWillScrollCallback \| undefined | 是 | onWillScroll事件的回调函数。 |

