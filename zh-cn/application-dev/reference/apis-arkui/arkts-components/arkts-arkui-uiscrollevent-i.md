# UIScrollEvent

frameNode中[getEvent('Scroll')](../arkts-apis/arkts-arkui-typenode-getevent-f.md) 方法的返回值，可用于给Scroll节点设置滚动事件。 UIScrollEvent继承于UIScrollableCommonEvent。

**继承/实现关系：** UIScrollEvent extends UIScrollableCommonEvent

**起始版本：** 19

<!--Device-unnamed-declare interface UIScrollEvent--><!--Device-unnamed-declare interface UIScrollEvent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## setOnDidScroll

```TypeScript
setOnDidScroll(callback: ScrollOnScrollCallback | undefined): void
```

onDidScroll事件的回调。 方法入参为undefined时，会重置事件回调。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-UIScrollEvent-setOnDidScroll(callback: ScrollOnScrollCallback | undefined): void--><!--Device-UIScrollEvent-setOnDidScroll(callback: ScrollOnScrollCallback | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [ScrollOnScrollCallback](arkts-arkui-scrollonscrollcallback-t.md) \| undefined | 是 | onDidScroll事件的回调函数。 |

## setOnWillScroll

```TypeScript
setOnWillScroll(callback: ScrollOnWillScrollCallback | undefined): void
```

onWillScroll事件的回调。 方法入参为undefined时，会重置事件回调。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-UIScrollEvent-setOnWillScroll(callback: ScrollOnWillScrollCallback | undefined): void--><!--Device-UIScrollEvent-setOnWillScroll(callback: ScrollOnWillScrollCallback | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [ScrollOnWillScrollCallback](arkts-arkui-scrollonwillscrollcallback-t.md) \| undefined | 是 | onWillScroll事件的回调函数。 |

