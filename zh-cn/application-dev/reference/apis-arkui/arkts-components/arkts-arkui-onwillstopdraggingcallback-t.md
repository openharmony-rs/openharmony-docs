# OnWillStopDraggingCallback

```TypeScript
declare type OnWillStopDraggingCallback = (velocity: number) => void
```

On scroll callback using in scrollable onWillStopDragging.

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本20开始，该接口支持在ArkTS卡片中使用。

<!--Device-unnamed-declare type OnWillStopDraggingCallback = (velocity: number) => void--><!--Device-unnamed-declare type OnWillStopDraggingCallback = (velocity: number) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| velocity | number | 是 | The veolicity of the scroll view at the moment the touch was released.  |

