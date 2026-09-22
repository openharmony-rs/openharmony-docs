# UIWaterFlowEvent

```TypeScript
declare interface UIWaterFlowEvent extends UIScrollableCommonEvent
```

frameNode中[getEvent('WaterFlow')](../arkts-apis/arkts-arkui-typenode-getevent-f.md#getevent-2)方法的返回值，可用于给WaterFlow节点设置滚动事件。

UIWaterFlowEvent继承于[UIScrollableCommonEvent](arkts-arkui-common-comp-uiscrollablecommonevent-i.md)。

**继承/实现关系：** UIWaterFlowEvent extends [UIScrollableCommonEvent](arkts-arkui-common-comp-uiscrollablecommonevent-i.md)

**起始版本：** 19

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## setOnDidScroll

```TypeScript
setOnDidScroll(callback: OnScrollCallback | undefined): void
```

设置onDidScroll事件的回调。

> **说明：** 
> 
> setOnWillScroll用于设置每帧滚动开始前的回调，setOnDidScroll用于设置每帧滚动完成后的回调。两者可同时使用，setOnWillScroll的回调先于setOnDidScroll触发。
> 方法入参为undefined时，会重置事件回调。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnScrollCallback](arkts-arkui-common-comp-onscrollcallback-t.md) &#124; undefined | 是 | onDidScroll事件的回调函数。 |

## setOnScrollIndex

```TypeScript
setOnScrollIndex(callback: OnWaterFlowScrollIndexCallback | undefined): void
```

设置[onScrollIndex](arkts-arkui-waterflow-comp-attribute.md#onscrollindex)事件的回调。

方法入参为undefined时，会重置事件回调。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnWaterFlowScrollIndexCallback](arkts-arkui-waterflow-comp-onwaterflowscrollindexcallback-t.md) &#124; undefined | 是 | onScrollIndex事件的回调函数。 |

## setOnWillScroll

```TypeScript
setOnWillScroll(callback: OnWillScrollCallback | undefined): void
```

设置onWillScroll事件的回调。

方法入参为undefined时，会重置事件回调。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnWillScrollCallback](arkts-arkui-common-comp-onwillscrollcallback-t.md) &#124; undefined | 是 | onWillScroll事件的回调函数。 |
