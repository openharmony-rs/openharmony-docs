# UIGridEvent

frameNode中[getEvent('Grid')](FrameNode:typeNode.getEvent(node: FrameNode, nodeType: 'Grid'))方法的返回值，可用于给Grid节点设置
滚动事件。

UIGridEvent继承于[UIScrollableCommonEvent](arkts-arkui-uiscrollablecommonevent-i.md)。

**继承/实现关系：** UIGridEvent extends [UIScrollableCommonEvent](arkts-arkui-uiscrollablecommonevent-i.md)

**起始版本：** 19

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## setOnDidScroll

```TypeScript
setOnDidScroll(callback: OnScrollCallback | undefined): void
```

设置[onDidScroll](../../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#ondidscroll12)事件的回调。

方法入参为undefined时，会重置事件回调。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本19开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | OnScrollCallback \| undefined | 是 | onDidScroll事件的回调函数。 |

## setOnScrollIndex

```TypeScript
setOnScrollIndex(callback: OnGridScrollIndexCallback | undefined): void
```

设置[onScrollIndex](../../../../reference/apis-arkui/arkui-ts/ts-container-grid.md#onscrollindex)事件的回调。

方法入参为undefined时，会重置事件回调。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本19开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | OnGridScrollIndexCallback \| undefined | 是 | onScrollIndex事件的回调函数。 |

## setOnWillScroll

```TypeScript
setOnWillScroll(callback: OnWillScrollCallback | undefined): void
```

设置[onWillScroll](../../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#onwillscroll12)事件的回调。

方法入参为undefined时，会重置事件回调。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本19开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | OnWillScrollCallback \| undefined | 是 | onWillScroll事件的回调函数。 |

