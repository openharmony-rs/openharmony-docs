# OnScrollCallback

```TypeScript
declare type OnScrollCallback = (scrollOffset: number, scrollState: ScrollState) => void
```

滚动组件滑动时触发的回调。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

<!--Device-unnamed-declare type OnScrollCallback = (scrollOffset: number, scrollState: ScrollState) => void--><!--Device-unnamed-declare type OnScrollCallback = (scrollOffset: number, scrollState: ScrollState) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| scrollOffset | number | 是 | 相对于上一帧的偏移量，滚动组件的内容向上滚动时偏移量为正，向下滚动时偏移量为负。\_\_\_HTML\_TAG\_USD\_0\_\_\_单位vp。  |
| scrollState | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 当前滑动状态。  |

