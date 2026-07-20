# UIListEvent

frameNode中[getEvent('List')](../arkts-apis/arkts-arkui-typenode-getevent-f.md#getevent-1)方法的返回值，可用于给List节点设置滚动事件。

UIListEvent继承于[UIScrollableCommonEvent](arkts-arkui-uiscrollablecommonevent-i.md)。

**继承/实现关系：** UIListEvent extends [UIScrollableCommonEvent](arkts-arkui-uiscrollablecommonevent-i.md)

**起始版本：** 19

<!--Device-unnamed-declare interface UIListEvent extends UIScrollableCommonEvent--><!--Device-unnamed-declare interface UIListEvent extends UIScrollableCommonEvent-End-->

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

<!--Device-UIListEvent-setOnDidScroll(callback: OnScrollCallback | undefined): void--><!--Device-UIListEvent-setOnDidScroll(callback: OnScrollCallback | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnScrollCallback](arkts-arkui-onscrollcallback-t.md) \| undefined | 是 | onDidScroll事件的回调函数。 |

<a id="setonscrollindex"></a>
## setOnScrollIndex

```TypeScript
setOnScrollIndex(callback: OnListScrollIndexCallback | undefined): void
```

设置[onScrollIndex](docroot://reference/apis-arkui/arkui-ts/ts-container-list.md#onscrollindex)事件的回调。

方法入参为undefined时，会重置事件回调。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-UIListEvent-setOnScrollIndex(callback: OnListScrollIndexCallback | undefined): void--><!--Device-UIListEvent-setOnScrollIndex(callback: OnListScrollIndexCallback | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnListScrollIndexCallback](arkts-arkui-onlistscrollindexcallback-t.md) \| undefined | 是 | onScrollIndex事件的回调函数。 |

<a id="setonscrollvisiblecontentchange"></a>
## setOnScrollVisibleContentChange

```TypeScript
setOnScrollVisibleContentChange(callback: OnScrollVisibleContentChangeCallback | undefined): void
```

设置[onScrollVisibleContentChange](ListAttribute#onScrollVisibleContentChange)事件的回调。

方法入参为undefined时，会重置事件回调。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-UIListEvent-setOnScrollVisibleContentChange(callback: OnScrollVisibleContentChangeCallback | undefined): void--><!--Device-UIListEvent-setOnScrollVisibleContentChange(callback: OnScrollVisibleContentChangeCallback | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnScrollVisibleContentChangeCallback](arkts-arkui-onscrollvisiblecontentchangecallback-t.md) \| undefined | 是 | onScrollVisibleContentChange事件的回调函数。 |

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

<!--Device-UIListEvent-setOnWillScroll(callback: OnWillScrollCallback | undefined): void--><!--Device-UIListEvent-setOnWillScroll(callback: OnWillScrollCallback | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnWillScrollCallback](arkts-arkui-onwillscrollcallback-t.md) \| undefined | 是 | onWillScroll事件的回调函数。 |

