# AccessibilityTransparentCallback

```TypeScript
declare type AccessibilityTransparentCallback = (event: TouchEvent) => void
```

提供开启朗读类辅助应用后未能被无障碍悬浮响应的触摸事件回调类型。

@typedef { function } AccessibilityTransparentCallback

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | [TouchEvent](arkts-arkui-touchevent-i.md) | 是 | 原始Touch事件对象，用于获取无法被无障碍悬浮识别为可聚焦组件的触摸事件的详细信息，包括触摸点坐标、触摸类型等属性。<br>**说明：** TouchEvent对象的触摸事件类型TouchType为四种无障碍悬浮事件类型中的一种，分别为HOVER_ENTER、HOVER_MOVE、HOVER_EXIT和HOVER_CANCEL。 |
