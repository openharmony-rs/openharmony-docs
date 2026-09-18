# @ohos.multimodalInput.inputEventClient(Input Event Injection)

The **inputEventClient** module provides the capability of injecting key, mouse/touchpad, and touchscreen events.

**Since:** 26.0.0

**System capability:** SystemCapability.MultimodalInput.Input.InputSimulator

## Modules to Import

```TypeScript
import { inputEventClient } from '@kit.InputKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [createKeyboardController](arkts-input-inputeventclient-createkeyboardcontroller-f.md) | Creates a keyboard controller for simulating key operations. This API uses a promise to return the result. |
| [createMouseController](arkts-input-inputeventclient-createmousecontroller-f.md) | Creates a mouse controller for simulating mouse operations. This API uses a promise to return the result. |
| [createTouchController](arkts-input-inputeventclient-createtouchcontroller-f.md) | Creates a touch controller for simulating touch operations. This API uses a promise to return the result. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [injectEvent](arkts-input-inputeventclient-injectevent-f-sys.md) | Injects keys (including single keys and combination keys). |
| [injectKeyEvent](arkts-input-inputeventclient-injectkeyevent-f-sys.md) | Injects key events (for both single keys and combination keys). |
| [injectMouseEvent](arkts-input-inputeventclient-injectmouseevent-f-sys.md) | Injects a mouse/touchpad event. |
| [injectTouchEvent](arkts-input-inputeventclient-injecttouchevent-f-sys.md) | Injects a touch event. |
| [permitInjection](arkts-input-inputeventclient-permitinjection-f-sys.md) | Specifies whether to authorize event injection. |
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
