# @ohos.multimodalInput.inputDevice(Input Device)

The inputDevice module implements input device management functions such as listening for the connection and disconnection of input devices and querying input device information such as the device name.

**Since:** 8

**System capability:** SystemCapability.MultimodalInput.Input.InputDevice

## Modules to Import

```TypeScript
import { inputDevice } from '@kit.InputKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getDevice](arkts-input-inputdevice-getdevice-f.md) | Obtains the information about the input device with the specified ID. This API uses an asynchronous callback to return the result. |
| [getDevice](arkts-input-inputdevice-getdevice-f.md) | Obtains the information about the input device with the specified ID. This API uses a promise to return the result. |
| [getDeviceIds](arkts-input-inputdevice-getdeviceids-f.md) | Obtains the IDs of all input devices. This API uses an asynchronous callback to return the result. |
| [getDeviceIds](arkts-input-inputdevice-getdeviceids-f.md) | Obtains the IDs of all input devices. This API uses a promise to return the result. |
| [getDeviceInfo](arkts-input-inputdevice-getdeviceinfo-f.md) | Obtains information about the specified input device. This API uses an asynchronous callback to return the result. |
| [getDeviceInfo](arkts-input-inputdevice-getdeviceinfo-f.md) | Obtains the information about the input device with the specified ID. This API uses a promise to return the result. |
| [getDeviceInfoSync](arkts-input-inputdevice-getdeviceinfosync-f.md) | Obtains information about the specified input device. |
| [getDeviceList](arkts-input-inputdevice-getdevicelist-f.md) | Obtains the IDs of all input devices. This API uses an asynchronous callback to return the result. |
| [getDeviceList](arkts-input-inputdevice-getdevicelist-f.md) | Obtains the IDs of all input devices. This API uses a promise to return the result. |
| [getIntervalSinceLastInput](arkts-input-inputdevice-getintervalsincelastinput-f.md) | Obtains the interval (including the device sleep time) elapsed since the last system input event. This API uses a promise to return the result. |
| [getKeyboardType](arkts-input-inputdevice-getkeyboardtype-f.md) | Obtains the keyboard type of the input device, such as full keyboard and numeric keypad. The keyboard type of the input device is subject to the result returned by this API. This API uses an asynchronous callback to return the result. |
| [getKeyboardType](arkts-input-inputdevice-getkeyboardtype-f.md) | Obtains the keyboard type of an input device. This API uses a promise to return the result. |
| [getKeyboardTypeSync](arkts-input-inputdevice-getkeyboardtypesync-f.md) | Obtains the keyboard type of the input device. |
| [isFunctionKeyEnabled](arkts-input-inputdevice-isfunctionkeyenabled-f.md) | Checks whether the specified function key (for example, **CapsLock**) is enabled. This API uses a promise to return the result. |
| [off](arkts-input-inputdevice-off-f.md#offchange) | Disables listening for device hot swap events. This API is called before the application exits. This API uses an asynchronous callback to return the result. |
| [on](arkts-input-inputdevice-on-f.md#onchange) | Enables listening for device hot swap events. When performing this operation, you need to connect to external devices such as a mouse, keyboard, and touchscreen. This API uses an asynchronous callback to return the result. |
| [setFunctionKeyEnabled](arkts-input-inputdevice-setfunctionkeyenabled-f.md) | Specifies whether to enable a function key (for example, **CapsLock**). This API uses a promise to return the result. |
| [supportKeys](arkts-input-inputdevice-supportkeys-f.md) | Queries whether a specified input device supports specified keys. This API uses an asynchronous callback to return the result. |
| [supportKeys](arkts-input-inputdevice-supportkeys-f.md) | Checks whether the input device supports the specified keys. This API uses a promise to return the result. |
| [supportKeysSync](arkts-input-inputdevice-supportkeyssync-f.md) | Checks whether the input device supports the specified keys. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [bindToDisplay](arkts-input-inputdevice-bindtodisplay-f-sys.md) | Bind input devices to a display group. Only external USB and Bluetooth mice, touchpads, keyboards, and game controllers are supported. After binding, the device will be fixed to operate on the display group where the specified display is located. This API uses a promise to return the result. |
| [getKeyboardRepeatDelay](arkts-input-inputdevice-getkeyboardrepeatdelay-f-sys.md) | Obtains the keyboard repeat delay. This API uses an asynchronous callback to return the result. |
| [getKeyboardRepeatDelay](arkts-input-inputdevice-getkeyboardrepeatdelay-f-sys.md) | Obtains the keyboard repeat delay. This API uses a promise to return the result. |
| [getKeyboardRepeatRate](arkts-input-inputdevice-getkeyboardrepeatrate-f-sys.md) | Obtains the keyboard repeat rate. This API uses an asynchronous callback to return the result. |
| [getKeyboardRepeatRate](arkts-input-inputdevice-getkeyboardrepeatrate-f-sys.md) | Obtains the keyboard repeat rate. This API uses a promise to return the result. |
| [setInputDeviceEnabled](arkts-input-inputdevice-setinputdeviceenabled-f-sys.md) | Sets the input switch status of an input device. Take the touchscreen as an example. If the input switch is off, the touchscreen does not respond when being touched. If the input switch is on, the touchscreen wakes up when being touched. This API uses a promise to return the result. |
| [setKeyboardRepeatDelay](arkts-input-inputdevice-setkeyboardrepeatdelay-f-sys.md) | Sets the keyboard repeat delay. This API uses an asynchronous callback to return the result. |
| [setKeyboardRepeatDelay](arkts-input-inputdevice-setkeyboardrepeatdelay-f-sys.md) | Sets the keyboard repeat delay. This API uses a promise to return the result. |
| [setKeyboardRepeatRate](arkts-input-inputdevice-setkeyboardrepeatrate-f-sys.md) | Sets the keyboard repeat rate. This API uses an asynchronous callback to return the result. |
| [setKeyboardRepeatRate](arkts-input-inputdevice-setkeyboardrepeatrate-f-sys.md) | Sets the keyboard repeat rate. This API uses a promise to return the result. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [AxisRange](arkts-input-inputdevice-axisrange-i.md) | Defines the axis range of an input device. |
| [DeviceListener](arkts-input-inputdevice-devicelistener-i.md) | Provides hot swap information about an input device. |
| [InputDeviceData](arkts-input-inputdevice-inputdevicedata-i.md) | Provides information about an input device. |

### Enums

| Name | Description |
| --- | --- |
| [FunctionKey](arkts-input-inputdevice-functionkey-e.md) | Enumerates function key types. |
| [KeyboardType](arkts-input-inputdevice-keyboardtype-e.md) | Enumerates keyboard types. |

### Types

| Name | Description |
| --- | --- |
| [AxisType](arkts-input-inputdevice-axistype-t.md) | Defines the axis type of an input device. |
| [ChangedType](arkts-input-inputdevice-changedtype-t.md) | Enumerates hot swap events. |
| [SourceType](arkts-input-inputdevice-sourcetype-t.md) | Input sources supported by the input device, including the keyboard, mouse, touchscreen, trackball, touchpad, and joystick. |
