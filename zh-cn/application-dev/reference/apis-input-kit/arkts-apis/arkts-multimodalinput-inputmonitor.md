# @ohos.multimodalInput.inputMonitor

输入监听模块，提供了监听输入设备事件的能力。输入设备事件当前包括触屏输入事件、鼠标输入事件和触控板输入事件。 > **说明：** > > - 本模块同时支持ArkTS-Dyn、ArkTS-Sta。 > > - 文档中“全局”表示整个触控屏或触控板。如监听全局触屏输入事件，表示触摸触控板任何位置时，整个触控板的触屏输入事件均被监听。 > > - 本模块接口均为系统接口。

**起始版本：** 7

**ArkTS模式：** ArkTS-Dyn起始版本为7；ArkTS-Sta起始版本为23。

<!--Device-unnamed-declare namespace inputMonitor--><!--Device-unnamed-declare namespace inputMonitor-End-->

**系统能力：** SystemCapability.MultimodalInput.Input.InputMonitor

**系统接口：** 此接口为系统接口。

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [off](arkts-input-inputmonitor-off-f-sys.md#off) | 取消监听全局触屏输入事件，使用callback异步回调。 |
| [off](arkts-input-inputmonitor-off-f-sys.md#off-1) | 取消监听全局鼠标事件。使用callback异步回调。 |
| [off](arkts-input-inputmonitor-off-f-sys.md#off-2) | 取消监听全局触控板的捏合事件。使用callback异步回调。 |
| [off](arkts-input-inputmonitor-off-f-sys.md#off-3) | 取消监听全局触控板的捏合事件。使用callback异步回调。 |
| [off](arkts-input-inputmonitor-off-f-sys.md#off-4) | 取消监听全局触控板的旋转事件。使用callback异步回调。 |
| [off](arkts-input-inputmonitor-off-f-sys.md#off-5) | 取消监听全局触控板的三指滑动事件。使用callback异步回调。 |
| [off](arkts-input-inputmonitor-off-f-sys.md#off-6) | 取消监听全局触控板的四指滑动事件。使用callback异步回调。 |
| [off](arkts-input-inputmonitor-off-f-sys.md#off-7) | 取消监听全局触控板的三指轻点事件。使用callback异步回调。 |
| [off](arkts-input-inputmonitor-off-f-sys.md#off-8) | 取消监听指纹手势输入事件。使用callback异步回调。 |
| [off](arkts-input-inputmonitor-off-f-sys.md#off-9) | 取消监听向内滑动事件。使用callback异步回调。 |
| [off](arkts-input-inputmonitor-off-f-sys.md#off-10) | 取消监听触摸屏滑动手势事件。使用callback异步回调。 |
| [off](arkts-input-inputmonitor-off-f-sys.md#off-11) | 取消监听触摸屏捏合手势事件。使用callback异步回调。 |
| [off](arkts-input-inputmonitor-off-f-sys.md#off-12) | 取消监听按键按下抬起事件。支持取消监听META\_\_\_ESCAPED\_UNDERSCORE\_\_\_LEFT键、META\_\_\_ESCAPED\_UNDERSCORE\_\_\_RIGHT键、电源键、音量键。需和inputMonitor.on('keyPressed')配套使用。使用callback异步回调。 |
| [offFingerprint](arkts-input-inputmonitor-offfingerprint-f-sys.md#offfingerprint) | 取消监听指纹手势输入事件。 |
| [offFourFingersSwipe](arkts-input-inputmonitor-offfourfingersswipe-f-sys.md#offfourfingersswipe) | 取消监听全局触控板的四指滑动事件。 |
| [offKeyPressed](arkts-input-inputmonitor-offkeypressed-f-sys.md#offkeypressed) | 取消监听按键按下抬起事件。支持取消监听META\_\_\_ESCAPED\_UNDERSCORE\_\_\_LEFT键、META\_\_\_ESCAPED\_UNDERSCORE\_\_\_RIGHT键、电源键、音量键。需和inputMonitor.on('keyPressed')配套使用。 |
| [offMouse](arkts-input-inputmonitor-offmouse-f-sys.md#offmouse) | 取消监听全局鼠标事件。 |
| [offPinch](arkts-input-inputmonitor-offpinch-f-sys.md#offpinch) | 取消监听全局触控板的捏合事件。 |
| [offPinch](arkts-input-inputmonitor-offpinch-f-sys.md#offpinch-1) | 取消监听全局触控板的捏合事件。 |
| [offRotate](arkts-input-inputmonitor-offrotate-f-sys.md#offrotate) | 取消监听全局触控板的旋转事件。 |
| [offSwipeInward](arkts-input-inputmonitor-offswipeinward-f-sys.md#offswipeinward) | 取消监听向内滑动事件。 |
| [offThreeFingersSwipe](arkts-input-inputmonitor-offthreefingersswipe-f-sys.md#offthreefingersswipe) | 取消监听全局触控板的三指滑动事件。 |
| [offThreeFingersTap](arkts-input-inputmonitor-offthreefingerstap-f-sys.md#offthreefingerstap) | 取消监听全局触控板的三指轻点事件。 |
| [offTouch](arkts-input-inputmonitor-offtouch-f-sys.md#offtouch) | 取消监听全局触屏事件。 |
| [offTouchscreenPinch](arkts-input-inputmonitor-offtouchscreenpinch-f-sys.md#offtouchscreenpinch) | 取消监听触摸屏捏合手势事件。 |
| [offTouchscreenSwipe](arkts-input-inputmonitor-offtouchscreenswipe-f-sys.md#offtouchscreenswipe) | 取消监听触摸屏滑动手势事件。 |
| [on](arkts-input-inputmonitor-on-f-sys.md#on) | 监听全局触屏输入事件，使用callback异步回调。 |
| [on](arkts-input-inputmonitor-on-f-sys.md#on-1) | 监听全局鼠标事件。使用callback异步回调。 |
| [on](arkts-input-inputmonitor-on-f-sys.md#on-2) | 监听鼠标事件，当鼠标移动至指定矩形区域内时，触发回调任务。使用callback异步回调。 |
| [on](arkts-input-inputmonitor-on-f-sys.md#on-3) | 监听全局触控板的捏合事件。使用callback异步回调。 |
| [on](arkts-input-inputmonitor-on-f-sys.md#on-4) | 监听全局触控板的捏合事件。使用callback异步回调。 |
| [on](arkts-input-inputmonitor-on-f-sys.md#on-5) | 监听全局触控板的旋转事件。使用callback异步回调。 |
| [on](arkts-input-inputmonitor-on-f-sys.md#on-6) | 监听全局触控板的三指滑动事件。使用callback异步回调。 |
| [on](arkts-input-inputmonitor-on-f-sys.md#on-7) | 监听全局触控板的四指滑动事件。使用callback异步回调。 |
| [on](arkts-input-inputmonitor-on-f-sys.md#on-8) | 监听全局触控板的三指轻点事件。使用callback异步回调。 |
| [on](arkts-input-inputmonitor-on-f-sys.md#on-9) | 监听指纹手势输入事件。使用callback异步回调。 |
| [on](arkts-input-inputmonitor-on-f-sys.md#on-10) | 监听向内滑动事件。使用callback异步回调。 |
| [on](arkts-input-inputmonitor-on-f-sys.md#on-11) | 监听触摸屏滑动手势事件。使用callback异步回调。 |
| [on](arkts-input-inputmonitor-on-f-sys.md#on-12) | 监听触摸屏捏合手势事件。使用callback异步回调。 |
| [on](arkts-input-inputmonitor-on-f-sys.md#on-13) | 监听指定按键的按下抬起事件，支持监听META\_\_\_ESCAPED\_UNDERSCORE\_\_\_LEFT键、META\_\_\_ESCAPED\_UNDERSCORE\_\_\_RIGHT键、电源键、音量键。使用callback异步回调。 |
| [onFingerprint](arkts-input-inputmonitor-onfingerprint-f-sys.md#onfingerprint) | 监听指纹手势输入事件。 |
| [onFourFingersSwipe](arkts-input-inputmonitor-onfourfingersswipe-f-sys.md#onfourfingersswipe) | 监听全局触控板的四指滑动事件。 |
| [onKeyPressed](arkts-input-inputmonitor-onkeypressed-f-sys.md#onkeypressed) | 监听指定按键的按下抬起事件，支持监听META\_\_\_ESCAPED\_UNDERSCORE\_\_\_LEFT键、META\_\_\_ESCAPED\_UNDERSCORE\_\_\_RIGHT键、电源键、音量键。 |
| [onMouse](arkts-input-inputmonitor-onmouse-f-sys.md#onmouse) | 监听全局鼠标事件。 |
| [onMouse](arkts-input-inputmonitor-onmouse-f-sys.md#onmouse-1) | 监听鼠标事件，当鼠标移动至指定矩形区域内时，触发回调任务。 |
| [onPinch](arkts-input-inputmonitor-onpinch-f-sys.md#onpinch) | 监听全局触控板的捏合事件。 |
| [onPinch](arkts-input-inputmonitor-onpinch-f-sys.md#onpinch-1) | 监听全局触控板的捏合事件。 |
| [onRotate](arkts-input-inputmonitor-onrotate-f-sys.md#onrotate) | 监听全局触控板的旋转事件。 |
| [onSwipeInward](arkts-input-inputmonitor-onswipeinward-f-sys.md#onswipeinward) | 监听向内滑动事件。 |
| [onThreeFingersSwipe](arkts-input-inputmonitor-onthreefingersswipe-f-sys.md#onthreefingersswipe) | 监听全局触控板的三指滑动事件。 |
| [onThreeFingersTap](arkts-input-inputmonitor-onthreefingerstap-f-sys.md#onthreefingerstap) | 监听全局触控板的三指轻点事件。 |
| [onTouch](arkts-input-inputmonitor-ontouch-f-sys.md#ontouch) | 监听全局触屏事件。 |
| [onTouchscreenPinch](arkts-input-inputmonitor-ontouchscreenpinch-f-sys.md#ontouchscreenpinch) | 监听触摸屏捏合手势事件。 |
| [onTouchscreenSwipe](arkts-input-inputmonitor-ontouchscreenswipe-f-sys.md#ontouchscreenswipe) | 监听触摸屏滑动手势事件。 |
| [queryTouchEvents](arkts-input-inputmonitor-querytouchevents-f-sys.md#querytouchevents) | 查询最近的触屏输入事件，最多支持查询100条事件，从API版本26.0.0开始，最多支持查询60条事件，使用Promise异步回调。 |
<!--DelEnd-->

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [TouchEventReceiver](arkts-input-inputmonitor-toucheventreceiver-t-sys.md) | 触屏输入事件的回调函数。 |
<!--DelEnd-->

