# @ohos.multimodalInput.inputMonitor

输入监听模块，提供了监听输入设备事件的能力。输入设备事件当前包括触屏输入事件、鼠标输入事件和触控板输入事件。

> **说明：**  
>  
> - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。  
>  
> - 文档中“全局”表示整个触控屏或触控板。如监听全局触屏输入事件，表示触摸触控板任何位置时，整个触控板的触屏输入事件均被监听。  
>  
> - 本模块接口均为系统接口。

**起始版本：** 7

<!--Device-unnamed-declare namespace inputMonitor--><!--Device-unnamed-declare namespace inputMonitor-End-->

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
| [off](arkts-input-inputmonitor-off-f-sys.md#off-1) | 取消监听全局触屏输入事件，使用callback异步回调。 |
| [off](arkts-input-inputmonitor-off-f-sys.md#off-2) | 取消监听全局鼠标事件。使用callback异步回调。 |
| [off](arkts-input-inputmonitor-off-f-sys.md#off-3) | 取消监听全局触控板的捏合事件。使用callback异步回调。 |
| [off](arkts-input-inputmonitor-off-f-sys.md#off-4) | 取消监听全局触控板的捏合事件。使用callback异步回调。 |
| [off](arkts-input-inputmonitor-off-f-sys.md#off-5) | 取消监听全局触控板的旋转事件。使用callback异步回调。 |
| [off](arkts-input-inputmonitor-off-f-sys.md#off-6) | 取消监听全局触控板的三指滑动事件。使用callback异步回调。 |
| [off](arkts-input-inputmonitor-off-f-sys.md#off-7) | 取消监听全局触控板的四指滑动事件。使用callback异步回调。 |
| [off](arkts-input-inputmonitor-off-f-sys.md#off-8) | 取消监听全局触控板的三指轻点事件。使用callback异步回调。 |
| [off](arkts-input-inputmonitor-off-f-sys.md#off-9) | 取消监听指纹手势输入事件。使用callback异步回调。 |
| [off](arkts-input-inputmonitor-off-f-sys.md#off-10) | 取消监听向内滑动事件。使用callback异步回调。 |
| [off](arkts-input-inputmonitor-off-f-sys.md#off-11) | 取消监听触摸屏滑动手势事件。使用callback异步回调。 |
| [off](arkts-input-inputmonitor-off-f-sys.md#off-12) | 取消监听触摸屏捏合手势事件。使用callback异步回调。 |
| [off](arkts-input-inputmonitor-off-f-sys.md#off-13) | 取消监听按键按下抬起事件。支持取消监听META_LEFT键、META_RIGHT键、电源键、音量键。需和inputMonitor.on('keyPressed')配套使用。使用callback异步回调。 |
| [on](arkts-input-inputmonitor-on-f-sys.md#on-1) | 监听全局触屏输入事件，使用callback异步回调。 |
| [on](arkts-input-inputmonitor-on-f-sys.md#on-2) | 监听全局鼠标事件。使用callback异步回调。 |
| [on](arkts-input-inputmonitor-on-f-sys.md#on-3) | 监听鼠标事件，当鼠标移动至指定矩形区域内时，触发回调任务。使用callback异步回调。 |
| [on](arkts-input-inputmonitor-on-f-sys.md#on-4) | 监听全局触控板的捏合事件。使用callback异步回调。 |
| [on](arkts-input-inputmonitor-on-f-sys.md#on-5) | 监听全局触控板的捏合事件。使用callback异步回调。 |
| [on](arkts-input-inputmonitor-on-f-sys.md#on-6) | 监听全局触控板的旋转事件。使用callback异步回调。 |
| [on](arkts-input-inputmonitor-on-f-sys.md#on-7) | 监听全局触控板的三指滑动事件。使用callback异步回调。 |
| [on](arkts-input-inputmonitor-on-f-sys.md#on-8) | 监听全局触控板的四指滑动事件。使用callback异步回调。 |
| [on](arkts-input-inputmonitor-on-f-sys.md#on-9) | 监听全局触控板的三指轻点事件。使用callback异步回调。 |
| [on](arkts-input-inputmonitor-on-f-sys.md#on-10) | 监听指纹手势输入事件。使用callback异步回调。 |
| [on](arkts-input-inputmonitor-on-f-sys.md#on-11) | 监听向内滑动事件。使用callback异步回调。 |
| [on](arkts-input-inputmonitor-on-f-sys.md#on-12) | 监听触摸屏滑动手势事件。使用callback异步回调。 |
| [on](arkts-input-inputmonitor-on-f-sys.md#on-13) | 监听触摸屏捏合手势事件。使用callback异步回调。 |
| [on](arkts-input-inputmonitor-on-f-sys.md#on-14) | 监听指定按键的按下抬起事件，支持监听META_LEFT键、META_RIGHT键、电源键、音量键。使用callback异步回调。 |
| [queryTouchEvents](arkts-input-inputmonitor-querytouchevents-f-sys.md#querytouchevents-1) | 查询最近的触屏输入事件，最多支持查询100条事件，从API版本26.0.0开始，最多支持查询60条事件，使用Promise异步回调。 |
<!--DelEnd-->

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [TouchEventReceiver](arkts-input-inputmonitor-toucheventreceiver-t-sys.md) | 触屏输入事件的回调函数。 |
<!--DelEnd-->

