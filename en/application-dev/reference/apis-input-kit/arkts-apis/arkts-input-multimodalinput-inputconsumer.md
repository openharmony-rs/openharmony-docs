# @ohos.multimodalInput.inputConsumer(Global Hotkeys)

The **inputConsumer** module implements listening for combination key events as well as listening and interception for volume key events.

> **NOTE:** 
> 
> - Global hotkeys are combination keys defined by the system or application. System hotkeys are defined by the system, and application hotkeys are defined by applications.

**Since:** 14

<!--Device-unnamed-declare namespace inputConsumer--><!--Device-unnamed-declare namespace inputConsumer-End-->

**System capability:** SystemCapability.MultimodalInput.Input.InputConsumer

## Modules to Import

```TypeScript
import { inputConsumer } from '@kit.InputKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getAllSystemHotkeys](arkts-input-inputconsumer-getallsystemhotkeys-f.md#getallsystemhotkeys) | Obtains all system hotkeys. This API uses a promise to return the result. |
| [off('hotkeyChange')](arkts-input-inputconsumer-off-f.md#offhotkeychange) | Unsubscribes from application hotkey change events. This API uses an asynchronous callback to return the result. |
| [off('keyPressed')](arkts-input-inputconsumer-off-f.md#offkeypressed) | Unsubscribes from key press events. This API uses an asynchronous callback to return the result. If the API call is successful, the system's default response to the key event will be resumed; that is, system-level actions, such as volume adjustment, will be triggered normally. |
| [on('hotkeyChange')](arkts-input-inputconsumer-on-f.md#onhotkeychange) | Subscribes to application hotkey change events. This API obtains combination key input events that meet the specified conditions, and uses an asynchronous callback to return the result. |
| [on('keyPressed')](arkts-input-inputconsumer-on-f.md#onkeypressed) | Subscribes to key press events. If the current application is in the foreground focus window, a callback is triggered when the specified key is pressed. This API uses an asynchronous callback to return the result. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getShieldStatus](arkts-input-inputconsumer-getshieldstatus-f-sys.md#getshieldstatus) | Obtains the system hotkey shield status. |
| [off('key')](arkts-input-inputconsumer-off-f-sys.md#offkey) | Unsubscribes from system hotkeys. This API uses an asynchronous callback to return the result. |
| [offKey](arkts-input-inputconsumer-offkey-f-sys.md#offkey2) | Unsubscribes from system hotkeys. This API uses an asynchronous callback to return the result. |
| [on('key')](arkts-input-inputconsumer-on-f-sys.md#onkey) | Subscribes to system hotkeys. This API uses an asynchronous callback to return the result. |
| [onKey](arkts-input-inputconsumer-onkey-f-sys.md#onkey2) | Subscribes to key combinations (key command mode). You can specify different trigger modes through triggerType. When a key combination input event that meets the conditions occurs, this API uses an asynchronous callback to return the result. |
| [setShieldStatus](arkts-input-inputconsumer-setshieldstatus-f-sys.md#setshieldstatus) | Sets the system hotkey shield status. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [HotkeyOptions](arkts-input-inputconsumer-hotkeyoptions-i.md) | Defines hotkey options. |
| [KeyPressedConfig](arkts-input-inputconsumer-keypressedconfig-i.md) | Sets the key event consumption configuration. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [KeyOptions](arkts-input-inputconsumer-keyoptions-i-sys.md) | Represents key combination options. |
<!--DelEnd-->

<!--Del-->
### Types(System API)

| Name | Description |
| --- | --- |
| [KeyCommandCallback](arkts-input-inputconsumer-keycommandcallback-t-sys.md) | Defines the key command callback function type, which is triggered when the hotkey registration conditions are met. |
<!--DelEnd-->

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [KeyCommandTriggerType](arkts-input-inputconsumer-keycommandtriggertype-e-sys.md) | Enumerates the key command trigger types, which are used to specify the trigger timing of key combinations. |
| [ShieldMode](arkts-input-inputconsumer-shieldmode-e-sys.md) | Enumerates system hotkey shield modes. |
<!--DelEnd-->
