# @ohos.multimodalInput.inputEvent (Input Event)

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=1a59b01eb09cbde916aad8893b634e85d3707880 translatedAt=2026-11-04T04:39:45.098Z pushedAt=2026-11-04T08:04:44.690Z nl=1 -->

The **inputEvent** module provides the basic events reported by the device.

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
| id         | number | No   | No   | Enumerates event IDs.|
| deviceId   | number | No   | No   | Unique ID of the input device. If a physical device is repeatedly reinstalled or restarted, its ID may change.   |
| actionTime | number | No    | No    | Time when an input event is reported, in microseconds (μs) since the system starts.    |
| screenId   | number | No   | No   | Target screen ID.        |
| windowId   | number | No   | No   | Target window ID.        |