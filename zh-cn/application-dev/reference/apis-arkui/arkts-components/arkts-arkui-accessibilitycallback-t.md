# AccessibilityCallback

```TypeScript
declare type AccessibilityCallback = (isHover: boolean, event: AccessibilityHoverEvent) => void
```

提供开启无障碍模式后的无障碍悬浮回调事件类型。

@typedef { function } AccessibilityCallback

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isHover | boolean | 是 | 表示开启无障碍模式后，手指在组件上触发由Touch事件转换成的无障碍悬浮事件，手指进入时为true，退出时为false。 |
| event | [AccessibilityHoverEvent](arkts-arkui-accessibilityhoverevent-i.md) | 是 | 无障碍悬浮事件对象，用于获取触发无障碍悬浮事件时的详细信息，包括无障碍悬浮动作类型（type）、手指相对于组件/窗口/屏幕的坐标（x、y、windowX、windowY、displayX、displayY、globalDisplayX、globalDisplayY）等属性。 |
