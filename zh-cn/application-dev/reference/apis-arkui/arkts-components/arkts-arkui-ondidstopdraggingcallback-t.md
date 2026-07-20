# OnDidStopDraggingCallback

```TypeScript
declare type OnDidStopDraggingCallback = (willFling: boolean) => void
```

On scroll callback using in scrollable onDidStopDragging.

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本21开始，该接口支持在ArkTS卡片中使用。

<!--Device-unnamed-declare type OnDidStopDraggingCallback = (willFling: boolean) => void--><!--Device-unnamed-declare type OnDidStopDraggingCallback = (willFling: boolean) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| willFling | boolean | 是 | whether start fling animation.  |

