# @ohos.multimodalInput.inputEvent (Input Event)

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=6ff193a1258b05452b4935e34a160adf6db64d7a translatedAt=2026-09-11T00:59:34.294Z pushedAt=2026-09-11T02:40:08.602Z -->

The **inputEvent** module provides the basic events reported by a device.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.

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
| actionTime | number | No    | No    | Time when an input event is reported, in microseconds (μs) since the system starts.    |
| screenId   | number | No   | No   | Target screen ID.        |
| windowId   | number | No   | No   | Target window ID.        |