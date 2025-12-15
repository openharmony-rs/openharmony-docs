# Input Device Development

<!--Kit: Input Kit-->
<!--Subsystem: MultimodalInput-->
<!--Owner: @zhaoxueyuan-->
<!--Designer: @hanruofei-->
<!--Tester: @Lyuxin-->
<!--Adviser: @Brilliantry_Rui-->

## When to Use

Input device management provides functions such as listening for device hot-swap events and querying the keyboard type of a specified device. For example, as a user enters text, the input method determines whether to launch the virtual keyboard based on whether a physical keyboard is currently inserted. Your application can determine whether a physical keyboard is inserted by listening to device hot-swap events.

## Modules to Import

```js
import { inputDevice } from '@kit.InputKit';
```

## Available APIs

The following table lists the common APIs for input device management. For details about the APIs, see [ohos.multimodalInput.inputDevice](../../reference/apis-input-kit/js-apis-inputdevice.md).

| API | Description|
| ----------- | ------------------------------------------------------------ | 
| getDeviceList(): Promise\<Array\<number>> | Obtains the list of input devices.|
| getKeyboardType(deviceId: number): Promise\<KeyboardType> | Obtains the keyboard type of the input device.|
| on(type: "change", listener: Callback\<DeviceListener>): void | Enables listening for device hot-swap events.|
| off(type: "change", listener?: Callback\<DeviceListener>): void | Disables listening for device hot-swap events.|

## Virtual Keyboard Detection

When a user enters text, the input method determines whether to launch the virtual keyboard based on whether a physical keyboard is currently inserted. Your application can determine whether a physical keyboard is inserted by listening to device hot-swap events.

### How to Develop

1. Call the [getDeviceList](../../reference/apis-input-kit/js-apis-inputdevice.md#inputdevicegetdevicelist9) API to obtain the list of connected input devices. Call the [getKeyboardType](../../reference/apis-input-kit/js-apis-inputdevice.md#inputdevicegetkeyboardtype9) API to traverse all connected devices to check whether a physical keyboard exists. If a physical keyboard exists, mark the physical keyboard as connected. This step ensures that your application detects all inserted input devices before listening for device hot-swap events.
2. Call the [on](../../reference/apis-input-kit/js-apis-inputdevice.md#inputdeviceon9) API to listen for device hot-swap events. If a physical keyboard is inserted, mark the physical keyboard as connected. If a physical keyboard is removed, mark the physical keyboard as disconnected.

<!-- @[input_device](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/input/ArkTSInputDevice/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
import { inputDevice } from '@kit.InputKit';
import hilog from '@ohos.hilog';

const DOMAIN = 0x0000;

@Entry
@Component
struct Index {
  @State isPhysicalKeyboardExist: boolean = false;
  @State message: string = "Click to obtain the device list and listen for device hot-swap events.";

// ···

  build() {
    RelativeContainer() {
      Column() {
		// ···

        Text(this.message)
          .onClick(() => {
            try {
              // 1. Obtain the list of input devices and check whether a physical keyboard is connected.
              inputDevice.getDeviceList().then(data => {
                for (let i = 0; i < data.length; ++i) {
                  inputDevice.getKeyboardType(data[i]).then(type => {
                    if (type === inputDevice.KeyboardType.ALPHABETIC_KEYBOARD) {
                      // The physical keyboard is connected.
                      this.isPhysicalKeyboardExist = true;
                    }
                  });
                }
              });
              // 2. Listen for device hot-swap events.
              inputDevice.on("change", (data) => {
                hilog.info(DOMAIN, 'InputDevice', `Device event info: %{public}s`, JSON.stringify(data));
                inputDevice.getKeyboardType(data.deviceId).then((type) => {
                  hilog.info(DOMAIN, 'InputDevice', 'The keyboard type is: %{public}d', type);
                  if (type === inputDevice.KeyboardType.ALPHABETIC_KEYBOARD && data.type == 'add') {
                    // The physical keyboard is inserted.
                    this.isPhysicalKeyboardExist = true;
                  } else if (type == inputDevice.KeyboardType.ALPHABETIC_KEYBOARD && data.type == 'remove') {
                    // The physical keyboard is removed.
                    this.isPhysicalKeyboardExist = false;
                  }
                });
              });
              this.message = "Enabling device status listening succeeded"
            } catch (error) {
              hilog.error(DOMAIN, 'InputDevice', `Execute failed, error: %{public}s`,
                JSON.stringify(error, ["code", "message"]));
              this.message = `Enabling device status listening failed. Error information: ${JSON.stringify(error, ["code", "message"]))}`
            }
          })
		// ···
      }
	// ···
    }
  }
}

```
