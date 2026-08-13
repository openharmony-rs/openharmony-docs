# OnWillScrollCallback

```TypeScript
export type OnWillScrollCallback = (scrollOffset: double, scrollState: ScrollState, scrollSource: ScrollSource) => (undefined | ScrollResult)
```

Called before scroll to allow developer to control real offset the Scrollable can scroll.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type OnWillScrollCallback = (scrollOffset: double, scrollState: ScrollState, scrollSource: ScrollSource) => (undefined | ScrollResult)--><!--Device-unnamed-export type OnWillScrollCallback = (scrollOffset: double, scrollState: ScrollState, scrollSource: ScrollSource) => (undefined | ScrollResult)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scrollOffset | double | 是 | offset this frame will scroll, which may or may not be reached. |
| scrollState | [ScrollState](../../apis-arkui/arkts-components/arkts-arkui-scrollstate-e.md) | 是 | current scroll state. |
| scrollSource | [ScrollSource](../../apis-arkui/arkts-apis/arkts-arkui-scrollsource-e.md) | 是 | source of current scroll. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| (undefined \| ScrollResult) | the remain offset for the scrollable, same as scrollOffset when no ScrollResult is returned. |

