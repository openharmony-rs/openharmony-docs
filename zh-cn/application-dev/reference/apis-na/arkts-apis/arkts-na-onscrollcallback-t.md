# OnScrollCallback

```TypeScript
export type OnScrollCallback = (scrollOffset: double, scrollState: ScrollState) => void
```

On scroll callback using in scrollable onDidScroll.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type OnScrollCallback = (scrollOffset: double, scrollState: ScrollState) => void--><!--Device-unnamed-export type OnScrollCallback = (scrollOffset: double, scrollState: ScrollState) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scrollOffset | double | 是 | offset this frame did scroll.  |
| scrollState | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | current scroll state.  |

