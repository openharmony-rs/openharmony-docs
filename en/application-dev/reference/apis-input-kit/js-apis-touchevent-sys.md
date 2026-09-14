# @ohos.multimodalInput.touchEvent (Touch Event) (System API)

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=6ff193a1258b05452b4935e34a160adf6db64d7a translatedAt=2026-09-11T01:31:12.885Z pushedAt=2026-09-11T03:19:01.377Z -->

The **touchEvent** module provides touch events reported by a device. It is inherited from [InputEvent](./js-apis-inputevent.md).

> **NOTE**
>
> - The initial APIs of this module are supported since API version 19. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - This topic describes only the system APIs provided by the module. For details about its public APIs, see [@ohos.multimodalInput.touchEvent (Touch Event)](js-apis-touchevent.md).

## Modules to Import

```js
import { FixedMode, Touch, TouchEvent } from '@kit.InputKit';
```

## FixedMode

Coordinate correction mode. The default value is NONE.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**System API**: This is a system API.

| Name         | Value | Description  |
| ------------ | ------ | ---- |
| NONE       |  0 | Normal mode.|
| AUTO |  1 | One-handed mode.|

## Touch

Defines the touch point information.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**System API**: This is a system API.

| Name         | Type  | Read-Only  | Optional  | Description                                 |
| ----------- | ------ | ---- | ---- | ----------------------------------- |
| fixedDisplayX | number | No | Yes | Correction value of the screenX coordinate in one-handed mode, in pixels. The default value is 0. |
| fixedDisplayY | number | No | Yes | Correction value of the screenY coordinate in one-handed mode, in pixels. The default value is 0. |
| blobId<sup>24+</sup> | number | No | Yes | Attribute identifier of the touch point. Currently, only single-finger touch is supported: the value is 1 for a left-hand touch and 2 for a right-hand touch. By default, the system automatically identifies the value. By default, this attribute is not set. |

## TouchEvent

Defines a touch event.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**System API**: This is a system API.

| Name        | Type      | Read-Only  | Optional  | Description       |
| ---------- | ---------- | ---- | ---- | --------- |
| fixedMode | [FixedMode](#fixedmode) | No | Yes | Coordinate correction mode. The default value is FixedMode.NONE.|
| isInject<sup>20+</sup> | boolean | No | Yes | Whether the touch event is an injection event. The default value is false. For details about injection events, see [@ohos.multimodalInput.inputEventClient](js-apis-inputeventclient-sys.md).|
