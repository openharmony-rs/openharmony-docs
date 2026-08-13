# UIScrollEvent

frameNode中getEvent('Scroll')方法的返回值，可用于给 Scroll节点设置滚动事件。 UIScrollEvent继承于UIScrollableCommonEvent。

**继承/实现关系：** UIScrollEvent extends UIScrollableCommonEvent

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-export declare interface UIScrollEvent--><!--Device-unnamed-export declare interface UIScrollEvent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## setOnDidScroll

```TypeScript
setOnDidScroll(callback: ScrollOnScrollCallback | undefined): void
```

设置onDidScroll事件的回调。 方法入参为undefined时，会重置事件回调。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIScrollEvent-setOnDidScroll(callback: ScrollOnScrollCallback | undefined): void--><!--Device-UIScrollEvent-setOnDidScroll(callback: ScrollOnScrollCallback | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [ScrollOnScrollCallback](arkts-na-scrollonscrollcallback-t.md) \| undefined | 是 | onDidScroll事件的回调函数。 |

## setOnWillScroll

```TypeScript
setOnWillScroll(callback: ScrollOnWillScrollCallback | undefined): void
```

设置onWillScroll事件的回调。 方法入参为undefined时，会重置事件回调。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-UIScrollEvent-setOnWillScroll(callback: ScrollOnWillScrollCallback | undefined): void--><!--Device-UIScrollEvent-setOnWillScroll(callback: ScrollOnWillScrollCallback | undefined): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [ScrollOnWillScrollCallback](arkts-na-scrollonwillscrollcallback-t.md) \| undefined | 是 | onWillScroll事件的回调函数。 |

