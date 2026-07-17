# WindowEventListener

```TypeScript
declare type WindowEventListener = (windowId: number, event: window.WindowEventType) => void
```

窗口事件的回调函数定义

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-declare type WindowEventListener = (windowId: int, event: window.WindowEventType) => void--><!--Device-unnamed-declare type WindowEventListener = (windowId: int, event: window.WindowEventType) => void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| windowId | int | 是 | 触发事件的窗口id |
| event | window.WindowEventType | 是 | 窗口回调的事件类型 |

