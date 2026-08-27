# @ohos.multimodalInput.inputMonitor(输入监听)

输入监听模块，提供了监听输入设备事件的能力。输入设备事件当前包括触屏输入事件、鼠标输入事件和触控板输入事件。

**起始版本：** 7

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| off(输入监听) | 取消监听全局触屏输入事件，使用callback异步回调。 |
| off(输入监听) | 取消监听全局鼠标事件。使用callback异步回调。 |
| off(输入监听) | 取消监听全局触控板的捏合事件。使用callback异步回调。 |
| off(输入监听) | 取消监听全局触控板的捏合事件。使用callback异步回调。 |
| off(输入监听) | 取消监听全局触控板的旋转事件。使用callback异步回调。 |
| [off(输入监听)](arkts-input-multimodalinput-gestureevent-threefingersswipe-i.md) | 取消监听全局触控板的三指滑动事件。使用callback异步回调。 |
| [off(输入监听)](arkts-input-multimodalinput-gestureevent-fourfingersswipe-i.md) | 取消监听全局触控板的四指滑动事件。使用callback异步回调。 |
| [off(输入监听)](arkts-input-multimodalinput-gestureevent-threefingerstap-i.md) | 取消监听全局触控板的三指轻点事件。使用callback异步回调。 |
| off(输入监听) | 取消监听指纹手势输入事件。使用callback异步回调。 |
| [off(输入监听)](arkts-input-multimodalinput-gestureevent-swipeinward-i-sys.md) | 取消监听向内滑动事件。使用callback异步回调。 |
| off(输入监听) | 取消监听触摸屏滑动手势事件。使用callback异步回调。 |
| off(输入监听) | 取消监听触摸屏捏合手势事件。使用callback异步回调。 |
| off(输入监听) | 取消监听按键按下抬起事件。支持取消监听META_LEFT键、META_RIGHT键、电源键、音量键。需和inputMonitor.on('keyPressed')配套使用。使用callback异步回调。 |
| on(输入监听) | 监听全局触屏输入事件，使用callback异步回调。 |
| on(输入监听) | 监听全局鼠标事件。使用callback异步回调。 |
| on(输入监听) | 监听鼠标事件，当鼠标移动至指定矩形区域内时，触发回调任务。使用callback异步回调。 |
| on(输入监听) | 监听全局触控板的捏合事件。使用callback异步回调。 |
| on(输入监听) | 监听全局触控板的捏合事件。使用callback异步回调。 |
| on(输入监听) | 监听全局触控板的旋转事件。使用callback异步回调。 |
| [on(输入监听)](arkts-input-multimodalinput-gestureevent-threefingersswipe-i.md) | 监听全局触控板的三指滑动事件。使用callback异步回调。 |
| [on(输入监听)](arkts-input-multimodalinput-gestureevent-fourfingersswipe-i.md) | 监听全局触控板的四指滑动事件。使用callback异步回调。 |
| [on(输入监听)](arkts-input-multimodalinput-gestureevent-threefingerstap-i.md) | 监听全局触控板的三指轻点事件。使用callback异步回调。 |
| on(输入监听) | 监听指纹手势输入事件。使用callback异步回调。 |
| [on(输入监听)](arkts-input-multimodalinput-gestureevent-swipeinward-i-sys.md) | 监听向内滑动事件。使用callback异步回调。 |
| on(输入监听) | 监听触摸屏滑动手势事件。使用callback异步回调。 |
| on(输入监听) | 监听触摸屏捏合手势事件。使用callback异步回调。 |
| on(输入监听) | 监听指定按键的按下抬起事件，支持监听META_LEFT键、META_RIGHT键、电源键、音量键。使用callback异步回调。 |
| [queryTouchEvents(输入监听)](arkts-input-inputmonitor-querytouchevents-f-sys.md) | 查询最近的触屏输入事件，最多支持查询100条事件，从API版本26.0.0开始，最多支持查询60条事件，使用Promise异步回调。 |
<!--DelEnd-->

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [TouchEventReceiver(输入监听)](arkts-input-inputmonitor-toucheventreceiver-t-sys.md) | 触屏输入事件的回调函数。 |
<!--DelEnd-->
