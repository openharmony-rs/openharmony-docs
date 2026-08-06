# UIGridEvent

frameNode中[getEvent('Grid')]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_方法的返 回值，可用于给Grid节点设置滚动事件。 UIGridEvent继承于[UIScrollableCommonEvent]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_。

**继承/实现关系：** UIGridEvent extends [UIScrollableCommonEvent](../../apis-na/arkts-apis/arkts-na-component/common-uiscrollablecommonevent-i.md)

**起始版本：** 19

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为19。

<!--Device-unnamed-declare interface UIGridEvent extends UIScrollableCommonEvent--><!--Device-unnamed-declare interface UIGridEvent extends UIScrollableCommonEvent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## setOnDidScroll

```TypeScript
setOnDidScroll(callback: OnScrollCallback | undefined): void
```

设置\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_事件的回调。 方法入参为undefined时，会重置事件回调。

**起始版本：** 19

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为19。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-UIGridEvent-setOnDidScroll(callback: OnScrollCallback | undefined): void--><!--Device-UIGridEvent-setOnDidScroll(callback: OnScrollCallback | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | onDidScroll事件的回调函数。传入undefined时，会重置事件回调。 |

## setOnScrollIndex

```TypeScript
setOnScrollIndex(callback: OnGridScrollIndexCallback | undefined): void
```

设置[onScrollIndex]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_事件的回调。 方法入参为undefined时，会重置事件回调。

**起始版本：** 19

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为19。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-UIGridEvent-setOnScrollIndex(callback: OnGridScrollIndexCallback | undefined): void--><!--Device-UIGridEvent-setOnScrollIndex(callback: OnGridScrollIndexCallback | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | onScrollIndex事件的回调函数。传入undefined时，会重置事件回调。 |

## setOnWillScroll

```TypeScript
setOnWillScroll(callback: OnWillScrollCallback | undefined): void
```

设置\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_事件的回调。 方法入参为undefined时，会重置事件回调。

**起始版本：** 19

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为19。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-UIGridEvent-setOnWillScroll(callback: OnWillScrollCallback | undefined): void--><!--Device-UIGridEvent-setOnWillScroll(callback: OnWillScrollCallback | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_ \| undefined | 是 | onWillScroll事件的回调函数。传入undefined时，会重置事件回调。 |

