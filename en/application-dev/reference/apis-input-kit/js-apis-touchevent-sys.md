# @ohos.multimodalInput.touchEvent (Touch Event) (System API)

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=574e1b97c419a831e3ff5b620b1254fe667a5306 translatedAt=2026-06-12T02:25:24.283Z pushedAt=2026-06-15T00:13:39.975Z -->

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

Enumerates coordinate correction modes.

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
| fixedDisplayX | number | No    | Yes    | Corrected value of the screenX coordinate in one-hand mode, in px. |
| fixedDisplayY | number | No    | Yes    | Corrected value of the screenY coordinate in one-hand mode, in px. |
| blobId<sup>24+</sup> | number | No   | Yes   | Touch point attribute ID. Currently, only single-finger touch is supported. The value **1** indicates left-hand touch, and the value **2** indicates right-hand touch.|

## TouchEvent

Defines a touch event.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**System API**: This is a system API.

| Name        | Type      | Read-Only  | Optional  | Description       |
| ---------- | ---------- | ---- | ---- | --------- |
| fixedMode  | [FixedMode](#fixedmode)   | No   | Yes   | Coordinate correction mode.|
| isInject<sup>20+</sup>  | boolean   | No   | Yes   | Whether the touch event is an injection event. For details about injection events, see [@ohos.multimodalInput.inputEventClient](js-apis-inputeventclient-sys.md).|