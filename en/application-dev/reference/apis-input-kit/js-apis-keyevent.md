# @ohos.multimodalInput.keyEvent (Key Event)

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @Brilliantry_Rui-->

The **keyEvent** module provides key events reported by a device. It is inherited from [InputEvent](js-apis-inputevent.md).

> **NOTE**
>
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```js
import { Action, Key, KeyEvent } from '@kit.InputKit';
```

## Action

Key event type.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.MultimodalInput.Input.Core

| Name  | Value | Description    |
| ------ | ------- | -------- |
| CANCEL | 0    | Cancellation of a key action.|
| DOWN   | 1    | Key press.|
| UP     | 2    | Key release.|

## Key

Defines a key.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.MultimodalInput.Input.Core

| Name       | Type| Read-Only| Optional| Description          |
| ----------- | -------- | ---- | ---- | -------------- |
| code        | [KeyCode](js-apis-keycode.md#keycode)  | No  | No  | Key code.        |
| pressedTime | number   | No  | No  | Key press time, in μs.|
| deviceId    | number   | No  | No  | Unique ID of the input device. If a physical device is repeatedly reinstalled or restarted, its ID may change.  |

## KeyEvent

Key event.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.MultimodalInput.Input.Core

| Name       | Type| Read-Only| Optional| Description                          |
| ----------- | -------- | ---- | ---- | ------------------------------ |
| action      | [Action](#action)   | No  | No  | Key event type.                      |
| key         | [Key](#key)      | No  | No  | Defines a key.            |
| unicodeChar | number   | No  | No  | Unicode character corresponding to the key.         |
| keys        | [Key](#key) []    | No  | No  | List of pressed keys.    |
| ctrlKey     | boolean  | No  | No  | Whether ctrlKey is being pressed.<br>The value **true** indicates that the key is pressed, and the value **false** indicates the opposite.|
| altKey      | boolean  | No  | No  | Whether altKey is being pressed.<br>The value **true** indicates that the key is pressed, and the value **false** indicates the opposite.    |
| shiftKey    | boolean  | No  | No  | Whether shiftKey is being pressed.<br>The value **true** indicates that the key is pressed, and the value **false** indicates the opposite.  |
| logoKey     | boolean  | No  | No  | Whether logoKey is being pressed.<br>The value **true** indicates that the key is pressed, and the value **false** indicates the opposite.   |
| fnKey       | boolean  | No  | No  | Whether fnKey is being pressed.<br>The value **true** indicates that the key is pressed, and the value **false** indicates the opposite.     |
| capsLock    | boolean  | No  | No  | Whether capsLock is enabled.<br>The value **true** indicates that capsLock is enabled, and the value **false** indicates the opposite.  |
| numLock     | boolean  | No  | No  | Whether numLock is enabled.<br>The value **true** indicates that numLock is enabled, and the value **false** indicates the opposite.   |
| scrollLock  | boolean  | No  | No  | Whether scrollLock is enabled.<br>The value **true** indicates that scrollLock is enabled, and the value **false** indicates the opposite.|
