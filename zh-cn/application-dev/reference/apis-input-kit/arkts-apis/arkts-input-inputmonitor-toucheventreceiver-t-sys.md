# TouchEventReceiver（系统接口）

```TypeScript
type TouchEventReceiver = (touchEvent: TouchEvent) => boolean
```

触屏输入事件的回调函数。

**起始版本：** 7

**ArkTS模式：** ArkTS-Dyn起始版本为7；ArkTS-Sta起始版本为23。

<!--Device-inputMonitor-type TouchEventReceiver = (touchEvent: TouchEvent) => boolean--><!--Device-inputMonitor-type TouchEventReceiver = (touchEvent: TouchEvent) => boolean-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| touchEvent | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 是 | 触屏输入事件。  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 若返回true，本次触屏后续产生的事件不再分发到窗口；若返回false，本次触屏后续产生的事件还会分发到窗口。 |

