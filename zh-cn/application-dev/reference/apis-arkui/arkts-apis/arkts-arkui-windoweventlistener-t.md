# WindowEventListener

```TypeScript
declare type WindowEventListener = (windowId: number, event: window.WindowEventType) => void
```

窗口生命周期事件通知的回调函数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| windowId | number | 是 | 触发事件的窗口id |
| event | [window.WindowEventType](arkts-arkui-window-windoweventtype-e.md) | 是 | 窗口回调的事件类型 |
