# OnScrollCallback

```TypeScript
declare type OnScrollCallback = (scrollOffset: number, scrollState: ScrollState) => void
```

On scroll callback using in scrollable onDidScroll.

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-unnamed-declare type OnScrollCallback = (scrollOffset: number, scrollState: ScrollState) => void--><!--Device-unnamed-declare type OnScrollCallback = (scrollOffset: number, scrollState: ScrollState) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scrollOffset | number | 是 | offset this frame did scroll.  |
| scrollState | [ScrollState](arkts-arkui-scrollstate-e.md) | 是 | current scroll state.  |

