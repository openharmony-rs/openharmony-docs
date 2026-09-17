# @ohos.multimodalInput.inputMonitor(Input Monitor)

The **inputMonitor** module implements listening for events of input devices, including the touchscreen, mouse, and touchpad.

> **NOTE:** 
> 
> - In this document, **global** indicates the entire touchscreen or touchpad. For example, listening for global touch events means to listen for touch events triggered when a user touches at any position on the touchpad.

**Since:** 7

**System capability:** SystemCapability.MultimodalInput.Input.InputMonitor

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { inputMonitor } from '@kit.InputKit';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [off](arkts-input-inputmonitor-off-f-sys.md#offtouch) | Cancels listening for global touchscreen input events. This API uses an asynchronous callback to return the result. |
| [off](arkts-input-inputmonitor-off-f-sys.md#offmouse) | Disables listening for global mouse events. This API uses an asynchronous callback to return the result. |
| [off](arkts-input-inputmonitor-off-f-sys.md#offpinch) | Disables listening for global touchpad pinch events. This API uses an asynchronous callback to return the result. |
| [off](arkts-input-inputmonitor-off-f-sys.md#offpinch) | Disables listening for global touchpad pinch events. This API uses an asynchronous callback to return the result. |
| [off](arkts-input-inputmonitor-off-f-sys.md#offrotate) | Disables listening for rotation events of the touchpad. This API uses an asynchronous callback to return the result. |
| [off](arkts-input-inputmonitor-off-f-sys.md#offthreefingersswipe) | Disables listening for three-finger swipe events. This API uses an asynchronous callback to return the result. |
| [off](arkts-input-inputmonitor-off-f-sys.md#offfourfingersswipe) | Disables listening for four-finger swipe events. This API uses an asynchronous callback to return the result. |
| [off](arkts-input-inputmonitor-off-f-sys.md#offthreefingerstap) | Disables listening for three-finger tap events. This API uses an asynchronous callback to return the result. |
| [off](arkts-input-inputmonitor-off-f-sys.md#offfingerprint) | Disables listening for fingerprint gesture input events. This API uses an asynchronous callback to return the result. |
| [off](arkts-input-inputmonitor-off-f-sys.md#offswipeinward) | Cancels listening for inward swipe events. This API uses an asynchronous callback to return the result. |
| [off](arkts-input-inputmonitor-off-f-sys.md#offtouchscreenswipe) | Disables listening for touchscreen swipe events. This API uses an asynchronous callback to return the result. |
| [off](arkts-input-inputmonitor-off-f-sys.md#offtouchscreenpinch) | Disables listening for touchscreen pinch events. This API uses an asynchronous callback to return the result. |
| [off](arkts-input-inputmonitor-off-f-sys.md#offkeypressed) | Cancels listening for the press and release events of the specified key, which can be the **META_LEFT**, **META_RIGHT**, power, or volume key. This API must be used together with **inputMonitor.on ('keyPressed')**. This API uses an asynchronous callback to return the result. |
| [on](arkts-input-inputmonitor-on-f-sys.md#ontouch) | Listens for global touchscreen input events. This API uses an asynchronous callback to return the result. |
| [on](arkts-input-inputmonitor-on-f-sys.md#onmouse) | Enables listening for global mouse events. This API uses an asynchronous callback to return the result. |
| [on](arkts-input-inputmonitor-on-f-sys.md#onmouse) | Enables listening for mouse events. When the mouse pointer moves to the specified rectangular area, a callback is triggered. This API uses an asynchronous callback to return the result. |
| [on](arkts-input-inputmonitor-on-f-sys.md#onpinch) | Enables listening for global touchpad pinch events. This API uses an asynchronous callback to return the result. |
| [on](arkts-input-inputmonitor-on-f-sys.md#onpinch) | Enables listening for global touchpad pinch events. This API uses an asynchronous callback to return the result. |
| [on](arkts-input-inputmonitor-on-f-sys.md#onrotate) | Enables listening for rotation events of the touchpad. This API uses an asynchronous callback to return the result. |
| [on](arkts-input-inputmonitor-on-f-sys.md#onthreefingersswipe) | Enables listening for three-finger swipe events. This API uses an asynchronous callback to return the result. |
| [on](arkts-input-inputmonitor-on-f-sys.md#onfourfingersswipe) | Enables listening for four-finger swipe events. This API uses an asynchronous callback to return the result. |
| [on](arkts-input-inputmonitor-on-f-sys.md#onthreefingerstap) | Enables listening for three-finger tap events. This API uses an asynchronous callback to return the result. |
| [on](arkts-input-inputmonitor-on-f-sys.md#onfingerprint) | Enables listening for fingerprint gesture input events. This API uses an asynchronous callback to return the result. |
| [on](arkts-input-inputmonitor-on-f-sys.md#onswipeinward) | Listens for inward swipe events. This API uses an asynchronous callback to return the result. |
| [on](arkts-input-inputmonitor-on-f-sys.md#ontouchscreenswipe) | Enables listening for touchscreen swipe events. This API uses an asynchronous callback to return the result. |
| [on](arkts-input-inputmonitor-on-f-sys.md#ontouchscreenpinch) | Enables listening for touchscreen pinch events. This API uses an asynchronous callback to return the result. |
| [on](arkts-input-inputmonitor-on-f-sys.md#onkeypressed) | Listens for the press and release events of the specified key, which can be the **META_LEFT**, **META_RIGHT**, power, or volume key. This API uses an asynchronous callback to return the result. |
| [queryTouchEvents](arkts-input-inputmonitor-querytouchevents-f-sys.md) | Queries recent touchscreen input events. A maximum of 100 events can be queried. Since API version 26.0.0, a maximum of 60 events can be queried. This API uses a promise to return the result. |
<!--DelEnd-->

<!--Del-->
### Types(System API)

| Name | Description |
| --- | --- |
| [TouchEventReceiver](arkts-input-inputmonitor-toucheventreceiver-t-sys.md) | Callback used to return the touch event. |
<!--DelEnd-->
