# OnDidStopDraggingCallback

```TypeScript
declare type OnDidStopDraggingCallback = (willFling: boolean) => void
```

滚动组件在结束拖拽时触发的回调。

**起始版本：** 21

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本21开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本21开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| willFling | boolean | 是 | 结束拖拽后是否会有惯性动效。返回true代表拖拽结束后有惯性动效，返回false代表没有惯性动效。 |
