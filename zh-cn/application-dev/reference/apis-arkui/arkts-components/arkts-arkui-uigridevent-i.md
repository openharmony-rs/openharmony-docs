# UIGridEvent

frameNode中[getEvent('Grid')](../arkts-apis/arkts-arkui-typenode-getevent-f.md)方法的返 回值，可用于给Grid节点设置滚动事件。UIGridEvent继承于[UIScrollableCommonEvent](arkts-arkui-uiscrollablecommonevent-i.md)。

**继承/实现关系：** UIGridEvent extends [UIScrollableCommonEvent](arkts-arkui-uiscrollablecommonevent-i.md)

**起始版本：** 19

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## setOnDidScroll

```TypeScript
setOnDidScroll(callback: OnScrollCallback | undefined): void
```

设置onDidScroll事件的回调。方法入参为undefined时，会重置事件回调。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnScrollCallback](arkts-arkui-onscrollcallback-t.md) \| undefined | 是 | onDidScroll事件的回调函数。传入undefined时，会重置事件回调。 |

## setOnScrollIndex

```TypeScript
setOnScrollIndex(callback: OnGridScrollIndexCallback | undefined): void
```

设置[onScrollIndex](arkts-arkui-grid-attribute.md#onscrollindex)事件的回调。方法入参为undefined时，会重置事件回调。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnGridScrollIndexCallback](arkts-arkui-ongridscrollindexcallback-t.md) \| undefined | 是 | onScrollIndex事件的回调函数。传入undefined时，会重置事件回调。 |

## setOnWillScroll

```TypeScript
setOnWillScroll(callback: OnWillScrollCallback | undefined): void
```

设置onWillScroll事件的回调。方法入参为undefined时，会重置事件回调。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [OnWillScrollCallback](arkts-arkui-onwillscrollcallback-t.md) \| undefined | 是 | onWillScroll事件的回调函数。传入undefined时，会重置事件回调。 |
