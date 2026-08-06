# OnWillScrollCallback

```TypeScript
declare type OnWillScrollCallback =
(scrollOffset: number, scrollState: ScrollState, scrollSource: ScrollSource) => void | ScrollResult
```

Called before scroll to allow developer to control real offset the Scrollable can scroll.

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type OnWillScrollCallback =(scrollOffset: number, scrollState: ScrollState, scrollSource: ScrollSource) => void | ScrollResult--><!--Device-unnamed-declare type OnWillScrollCallback =(scrollOffset: number, scrollState: ScrollState, scrollSource: ScrollSource) => void | ScrollResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scrollOffset | number | 是 | offset this frame will scroll, which may or may not be reached.  |
| scrollState | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | current scroll state.  |
| scrollSource | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | source of current scroll.  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| void \| ScrollResult | the remain offset for the scrollable, |

