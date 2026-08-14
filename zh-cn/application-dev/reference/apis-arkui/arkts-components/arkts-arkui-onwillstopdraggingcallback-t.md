# OnWillStopDraggingCallback

```TypeScript
declare type OnWillStopDraggingCallback = (velocity: number) => void
```

滚动组件划动离手时触发的回调。

**起始版本：** 20

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为20。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本20开始，该接口支持在ArkTS卡片中使用。

<!--Device-unnamed-declare type OnWillStopDraggingCallback = (velocity: number) => void--><!--Device-unnamed-declare type OnWillStopDraggingCallback = (velocity: number) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| velocity | number | 是 | 划动离手速度，滚动组件的内容向上滚动时速度为正，向下滚动时速度为负。<br/>单位vp/s。 |

