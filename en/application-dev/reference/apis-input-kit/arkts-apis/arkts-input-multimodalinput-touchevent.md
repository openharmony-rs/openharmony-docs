# @ohos.multimodalInput.touchEvent(Touch Event)

The **touchEvent** module provides touch events reported by a device. It is inherited from
 [InputEvent](arkts-input-multimodalinput-inputevent-inputevent-i.md).



## Modules to Import

```TypeScript
import { Action as KeyAction, SourceType, ToolType, Touch, TouchEvent, FixedMode } from '@kit.InputKit';
```

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [Touch](arkts-input-multimodalinput-touchevent-touch-i.md) | Defines the touch point information. |
| [TouchEvent](arkts-input-multimodalinput-touchevent-touchevent-i.md) | Defines a touch event. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [Touch](arkts-input-multimodalinput-touchevent-touch-i-sys.md) | Defines the touch point information. |
| [TouchEvent](arkts-input-multimodalinput-touchevent-touchevent-i-sys.md) | Defines a touch event. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [Action](arkts-input-multimodalinput-touchevent-action-e.md) | Enumerates the touch event types. |
| [SourceType](arkts-input-multimodalinput-touchevent-sourcetype-e.md) | Enumerates touch sources. Currently, only the touchscreen and touchpad are supported. |
| [ToolType](arkts-input-multimodalinput-touchevent-tooltype-e.md) | Enumerates touch tool types. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [FixedMode](arkts-input-multimodalinput-touchevent-fixedmode-e-sys.md) | Enumerates coordinate correction modes. |
<!--DelEnd-->
