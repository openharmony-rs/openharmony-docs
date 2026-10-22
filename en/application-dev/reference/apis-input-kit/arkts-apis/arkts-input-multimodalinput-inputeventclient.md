# @ohos.multimodalInput.inputEventClient(Input Event Injection)

The inputEventClient module provides the capability to inject input events, including key, mouse/touchpad, and touchscreen events.

**Since:** 26.0.0

<!--Device-unnamed-declare namespace inputEventClient--><!--Device-unnamed-declare namespace inputEventClient-End-->

**System capability:** SystemCapability.MultimodalInput.Input.InputSimulator

## Modules to Import

```TypeScript
import { inputEventClient } from '@kit.InputKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [createKeyboardController](arkts-input-inputeventclient-createkeyboardcontroller-f.md#createkeyboardcontroller-1) | Creates a keyboard controller for simulating key operations. This API uses a promise to return the result. |
| [createMouseController](arkts-input-inputeventclient-createmousecontroller-f.md#createmousecontroller-1) | Creates a mouse controller for simulating mouse operations. This API uses a promise to return the result. |
| [createTouchController](arkts-input-inputeventclient-createtouchcontroller-f.md#createtouchcontroller-1) | Creates a touch controller for simulating touch operations. This API uses a promise to return the result. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [injectEvent](arkts-input-inputeventclient-injectevent-f-sys.md#injectevent-1) | Injects keys (including single keys and combination keys). Since API version 26.0.1, the caller can specify the display ID for injecting a key event. If the specified display ID does not exist, the operation will not take effect. If displayId is not specified, the operation will take effect on the display group of the same user as the caller. |
| [injectKeyEvent](arkts-input-inputeventclient-injectkeyevent-f-sys.md#injectkeyevent-1) | Injects key events (for both single keys and combination keys). Since API version 26.0.1, the caller can specify the display ID for injecting a key event. If the specified display ID does not exist, the operation will not take effect. If displayId is not specified, the operation will take effect on the display group of the same user as the caller. |
| [injectMouseEvent](arkts-input-inputeventclient-injectmouseevent-f-sys.md#injectmouseevent-1) | Injects a mouse/touchpad event. |
| [injectTouchEvent](arkts-input-inputeventclient-injecttouchevent-f-sys.md#injecttouchevent-1) | Injects a touch event. |
| [permitInjection](arkts-input-inputeventclient-permitinjection-f-sys.md#permitinjection-1) | Specifies whether to authorize event injection. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [KeyboardController](arkts-input-inputeventclient-keyboardcontroller-i.md) | Provides the capability of simulating key operations. The simulated key operation sequence must meet the following requirements: |
| [MouseController](arkts-input-inputeventclient-mousecontroller-i.md) | Provides the capability of simulating mouse operations. The simulated mouse operation sequence must meet the following requirements: |
| [TouchController](arkts-input-inputeventclient-touchcontroller-i.md) | Provides the capability of simulating touch operations. The simulated touch operation sequence must meet the following requirements: |
| [TouchPoint](arkts-input-inputeventclient-touchpoint-i.md) | Represents information about a single touch point on the display. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [KeyEvent](arkts-input-inputeventclient-keyevent-i-sys.md) | Defines the key event to inject. |
| [KeyEventData](arkts-input-inputeventclient-keyeventdata-i-sys.md) | Defines the key event to inject. |
| [KeyEventInfo](arkts-input-inputeventclient-keyeventinfo-i-sys.md) | Defines the key event information injected by the user. |
| [MouseEventData](arkts-input-inputeventclient-mouseeventdata-i-sys.md) | Defines the mouse event data. |
| [TouchEventData](arkts-input-inputeventclient-toucheventdata-i-sys.md) | Defines the touch event data. |
<!--DelEnd-->
