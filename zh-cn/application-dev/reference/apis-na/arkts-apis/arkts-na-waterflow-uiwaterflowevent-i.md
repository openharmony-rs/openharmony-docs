# UIWaterFlowEvent

frameNode中getEvent('WaterFlow')方法的返回 值，可用于给WaterFlow节点设置滚动事件。 UIWaterFlowEvent继承于UIScrollableCommonEvent。

**继承/实现关系：** UIWaterFlowEvent extends UIScrollableCommonEvent

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

<!--Device-unnamed-export declare interface UIWaterFlowEvent--><!--Device-unnamed-export declare interface UIWaterFlowEvent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## setOnDidScroll

```TypeScript
setOnDidScroll(callback: OnScrollCallback | undefined): void
```

设置[onDidScroll](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#ondidscroll12)事件的回调。 方法入参为undefined时，会重置事件回调。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIWaterFlowEvent-setOnDidScroll(callback: OnScrollCallback | undefined): void--><!--Device-UIWaterFlowEvent-setOnDidScroll(callback: OnScrollCallback | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnScrollCallback](../../apis-arkui/arkts-components/arkts-arkui-onscrollcallback-t.md) \| undefined | 是 | onDidScroll事件的回调函数。 |

## setOnScrollIndex

```TypeScript
setOnScrollIndex(callback: OnWaterFlowScrollIndexCallback | undefined): void
```

设置onScrollIndex事件的回调。 方法入参为undefined时，会重置事件回调。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIWaterFlowEvent-setOnScrollIndex(callback: OnWaterFlowScrollIndexCallback | undefined): void--><!--Device-UIWaterFlowEvent-setOnScrollIndex(callback: OnWaterFlowScrollIndexCallback | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnWaterFlowScrollIndexCallback](arkts-na-onwaterflowscrollindexcallback-t.md) \| undefined | 是 | onScrollIndex事件的回调函数。 |

## setOnWillScroll

```TypeScript
setOnWillScroll(callback: OnWillScrollCallback | undefined): void
```

设置[onWillScroll](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#onwillscroll12)事件的回调。 方法入参为undefined时，会重置事件回调。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIWaterFlowEvent-setOnWillScroll(callback: OnWillScrollCallback | undefined): void--><!--Device-UIWaterFlowEvent-setOnWillScroll(callback: OnWillScrollCallback | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnWillScrollCallback](../../apis-arkui/arkts-components/arkts-arkui-onwillscrollcallback-t.md) \| undefined | 是 | onWillScroll事件的回调函数。 |

