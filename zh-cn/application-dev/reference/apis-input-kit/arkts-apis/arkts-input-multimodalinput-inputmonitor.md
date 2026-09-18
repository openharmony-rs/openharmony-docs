# @ohos.multimodalInput.inputMonitor(输入监听)

输入监听模块，提供了监听输入设备事件的能力。输入设备事件当前包括触屏输入事件、鼠标输入事件和触控板输入事件。

**起始版本：** 7

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { inputMonitor } from '@kit.InputKit';
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [off](arkts-input-inputmonitor-off-f-sys.md#offtouch) | 取消监听全局触屏输入事件，使用callback异步回调。 |
| [off](arkts-input-inputmonitor-off-f-sys.md#offmouse) | 取消监听全局鼠标事件。使用callback异步回调。 |
| [off](arkts-input-inputmonitor-off-f-sys.md#offpinch) | 取消监听全局触控板的捏合事件。使用callback异步回调。 |
| [off](arkts-input-inputmonitor-off-f-sys.md#offpinch) | 取消监听全局触控板的捏合事件。使用callback异步回调。 |
| [off](arkts-input-inputmonitor-off-f-sys.md#offrotate) | 取消监听全局触控板的旋转事件。使用callback异步回调。 |
| [off](arkts-input-inputmonitor-off-f-sys.md#offthreefingersswipe) | 取消监听全局触控板的三指滑动事件。使用callback异步回调。 |
| [off](arkts-input-inputmonitor-off-f-sys.md#offfourfingersswipe) | 取消监听全局触控板的四指滑动事件。使用callback异步回调。 |
| [off](arkts-input-inputmonitor-off-f-sys.md#offthreefingerstap) | 取消监听全局触控板的三指轻点事件。使用callback异步回调。 |
| [off](arkts-input-inputmonitor-off-f-sys.md#offfingerprint) | 取消监听指纹手势输入事件。使用callback异步回调。 |
| [off](arkts-input-inputmonitor-off-f-sys.md#offswipeinward) | 取消监听向内滑动事件。使用callback异步回调。 |
| [off](arkts-input-inputmonitor-off-f-sys.md#offtouchscreenswipe) | 取消监听触摸屏滑动手势事件。使用callback异步回调。 |
| [off](arkts-input-inputmonitor-off-f-sys.md#offtouchscreenpinch) | 取消监听触摸屏捏合手势事件。使用callback异步回调。 |
| [off](arkts-input-inputmonitor-off-f-sys.md#offkeypressed) | 取消监听按键按下抬起事件。支持取消监听META_LEFT键、META_RIGHT键、电源键、音量键。需和inputMonitor.on('keyPressed')配套使用。使用callback异步回调。 |
| [on](arkts-input-inputmonitor-on-f-sys.md#ontouch) | 监听全局触屏输入事件，使用callback异步回调。 |
| [on](arkts-input-inputmonitor-on-f-sys.md#onmouse) | 监听全局鼠标事件。使用callback异步回调。 |
| [on](arkts-input-inputmonitor-on-f-sys.md#onmouse) | 监听鼠标事件，当鼠标移动至指定矩形区域内时，触发回调任务。使用callback异步回调。 |
| [on](arkts-input-inputmonitor-on-f-sys.md#onpinch) | 监听全局触控板的捏合事件。使用callback异步回调。 |
| [on](arkts-input-inputmonitor-on-f-sys.md#onpinch) | 监听全局触控板的捏合事件。使用callback异步回调。 |
| [on](arkts-input-inputmonitor-on-f-sys.md#onrotate) | 监听全局触控板的旋转事件。使用callback异步回调。 |
| [on](arkts-input-inputmonitor-on-f-sys.md#onthreefingersswipe) | 监听全局触控板的三指滑动事件。使用callback异步回调。 |
| [on](arkts-input-inputmonitor-on-f-sys.md#onfourfingersswipe) | 监听全局触控板的四指滑动事件。使用callback异步回调。 |
| [on](arkts-input-inputmonitor-on-f-sys.md#onthreefingerstap) | 监听全局触控板的三指轻点事件。使用callback异步回调。 |
| [on](arkts-input-inputmonitor-on-f-sys.md#onfingerprint) | 监听指纹手势输入事件。使用callback异步回调。 |
| [on](arkts-input-inputmonitor-on-f-sys.md#onswipeinward) | 监听向内滑动事件。使用callback异步回调。 |
| [on](arkts-input-inputmonitor-on-f-sys.md#ontouchscreenswipe) | 监听触摸屏滑动手势事件。使用callback异步回调。 |
| [on](arkts-input-inputmonitor-on-f-sys.md#ontouchscreenpinch) | 监听触摸屏捏合手势事件。使用callback异步回调。 |
| [on](arkts-input-inputmonitor-on-f-sys.md#onkeypressed) | 监听指定按键的按下抬起事件，支持监听META_LEFT键、META_RIGHT键、电源键、音量键。使用callback异步回调。 |
| [queryTouchEvents](arkts-input-inputmonitor-querytouchevents-f-sys.md) | 查询最近的触屏输入事件，最多支持查询100条事件，从API版本26.0.0开始，最多支持查询60条事件，使用Promise异步回调。 |
<!--DelEnd-->

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [TouchEventReceiver](arkts-input-inputmonitor-toucheventreceiver-t-sys.md) | 触屏输入事件的回调函数。 |
<!--DelEnd-->
