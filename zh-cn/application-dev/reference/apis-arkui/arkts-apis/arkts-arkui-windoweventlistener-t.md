# WindowEventListener

```TypeScript
declare type WindowEventListener = (windowId: int, event: window.WindowEventType) => void
```

窗口生命周期事件通知的回调函数。

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-declare type WindowEventListener = (windowId: int, event: window.WindowEventType) => void--><!--Device-unnamed-declare type WindowEventListener = (windowId: int, event: window.WindowEventType) => void-End-->

**系统能力：** SystemCapability.Window.SessionManager

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| windowId | ArkTS-Dyn: number  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：int | 是 | 触发事件的窗口id  |
| event | window.WindowEventType | 是 | 窗口回调的事件类型  |

