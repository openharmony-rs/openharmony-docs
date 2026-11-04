# @ohos.multimodalInput.touchEvent (Touch Event) (System API)

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=1a59b01eb09cbde916aad8893b634e85d3707880 translatedAt=2026-11-04T04:53:03.196Z pushedAt=2026-11-04T08:04:44.714Z nl=1 -->

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

Enumerates the modes for correcting coordinates. The default value is NONE.

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
| fixedDisplayX | number | No | Yes | Correction value of the screenX coordinate in one-hand mode, in pixels (px). The default value is 0. |
| fixedDisplayY | number | No | Yes | Correction value of the screenY coordinate in one-hand mode, in pixels (px). The default value is 0. |
| blobId<sup>24+</sup> | number | No | Yes | Attribute identifier of the touch point. Currently, only single-finger touch is supported: 1 for left-hand touch and 2 for right-hand touch. The default value is automatically identified by the system. By default, this attribute is not set. |

## TouchEvent

Defines a touch event.

**System capability**: SystemCapability.MultimodalInput.Input.Core

**System API**: This is a system API.

| Name        | Type      | Read-Only  | Optional  | Description       |
| ---------- | ---------- | ---- | ---- | --------- |
| fixedMode | [FixedMode](#fixedmode) | No | Yes | Mode for correcting coordinates. The default value is FixedMode.NONE. |
| isInject<sup>20+</sup> | boolean | No | Yes | Indicates whether the touch input event is an injected event. The default value is false. For details about injected events, see [@ohos.multimodalInput.inputEventClient](js-apis-inputeventclient-sys.md). |
