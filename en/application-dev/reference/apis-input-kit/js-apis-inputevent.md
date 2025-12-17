# @ohos.multimodalInput.inputEvent (Input Event)

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @Brilliantry_Rui-->

The **inputEvent** module provides the basic events reported by the device.

> **NOTE**
>
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```js
import { InputEvent } from '@kit.InputKit';
```

## InputEvent 

Represents an input event.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.MultimodalInput.Input.Core

| Name        | Type  | Read-Only  | Optional  | Description            |
| ---------- | ------ | ---- | ---- | -------------- |
| id         | number | No   | No   | Event ID.|
| deviceId   | number | No   | No   | Unique ID of the input device. If a physical device is repeatedly reinstalled or restarted, its ID may change.   |
| actionTime | number | No   | No   | Time when the input event is reported.     |
| screenId   | number | No   | No   | ID of the target screen.        |
| windowId   | number | No   | No   | ID of the target window.        |
