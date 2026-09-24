# @ohos.multimodalInput.inputConsumer(Global Shortcut Keys)

The **inputConsumer** module implements listening for combination key events as well as listening and interception for volume key events.

> **NOTE:** 
> 
> - Global shortcut keys are combination keys defined by the system or application. System shortcut keys are defined by the system, and application shortcut keys are defined by applications.

**Since:** 14

**System capability:** SystemCapability.MultimodalInput.Input.InputConsumer

## Modules to Import

```TypeScript
import { inputConsumer } from '@kit.InputKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getAllSystemHotkeys](arkts-input-inputconsumer-getallsystemhotkeys-f.md) | Obtains all system shortcut keys. This API uses a promise to return the result. |
| [off](arkts-input-inputconsumer-off-f.md#offhotkeychange) | Unsubscribes from application shortcut key change events. This API uses an asynchronous callback to return the result. |
| [off](arkts-input-inputconsumer-off-f.md#offkeypressed) | Unsubscribes from key press events. This API uses an asynchronous callback to return the result. If the API call is successful, the system's default response to the key event will be resumed; that is, system-level actions, such as volume adjustment, will be triggered normally. |
| [on](arkts-input-inputconsumer-on-f.md#onhotkeychange) | Subscribes to application shortcut key change events. This API obtains combination key input events that meet the specified conditions, and uses an asynchronous callback to return the result. |
| [on](arkts-input-inputconsumer-on-f.md#onkeypressed) | Subscribes to key press events. If the current application is in the foreground focus window, a callback is triggered when the specified key is pressed. This API uses an asynchronous callback to return the result. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getShieldStatus](arkts-input-inputconsumer-getshieldstatus-f-sys.md) | Obtains the system hotkey shield status. |
| [off](arkts-input-inputconsumer-off-f-sys.md#offkey) | Disables listening for system hotkey change events. This API uses an asynchronous callback to return the result. |
| [offKey](arkts-input-inputconsumer-offkey-f-sys.md#offkey-1) | Unsubscribe system keys. |
| [on](arkts-input-inputconsumer-on-f-sys.md#onkey) | Enables listening for system hotkey change events. This API uses an asynchronous callback to return the system hotkey data when a system hotkey event that meets the specified condition occurs. |
| [onKey](arkts-input-inputconsumer-onkey-f-sys.md#onkey-1) | Subscribe system keys. |
| [setShieldStatus](arkts-input-inputconsumer-setshieldstatus-f-sys.md) | Sets the system hotkey shield status. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [HotkeyOptions](arkts-input-inputconsumer-hotkeyoptions-i.md) | Defines shortcut key options. |
| [KeyPressedConfig](arkts-input-inputconsumer-keypressedconfig-i.md) | Sets the key event consumption configuration. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [KeyOptions](arkts-input-inputconsumer-keyoptions-i-sys.md) | Represents combination key options. |
<!--DelEnd-->

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [KeyCommandTriggerType](arkts-input-inputconsumer-keycommandtriggertype-e-sys.md) | [KeyCommandTriggerType](arkts-input-inputconsumer-keycommandtriggertype-e-sys.md) |
| [ShieldMode](arkts-input-inputconsumer-shieldmode-e-sys.md) | Enumerates shortcut key shield modes. |
<!--DelEnd-->

<!--Del-->
### Types(System API)

| Name | Description |
| --- | --- |
| [KeyCommandCallback](arkts-input-inputconsumer-keycommandcallback-t-sys.md) | Callback function when the shortcut key registered by the system application meets the conditions. |
<!--DelEnd-->
