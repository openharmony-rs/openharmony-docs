# Switching Audio Input Devices
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

Starting from API version 21, support for switching audio input device routes is available.

When an application performs audio input, the system selects the corresponding input device based on the audio stream type. (If the audio stream type is **SOURCE_TYPE_MIC**, the built-in microphone is used for recording. If the audio stream type is **SOURCE_TYPE_VOICE_COMMUNICATION**, the input device follows the current output device.) If the default input device does not meet the application requirements, the application can call [setBluetoothAndNearlinkPreferredRecordCategory](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#setbluetoothandnearlinkpreferredrecordcategory21) or [selectMediaInputDevice](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#selectmediainputdevice21) to switch the audio input device.

## Preferring Bluetooth or NearLink Devices for Recording

Applications can use [setBluetoothAndNearlinkPreferredRecordCategory](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#setbluetoothandnearlinkpreferredrecordcategory21) of AudioSessionManager to express a preference for Bluetooth or NearLink devices when they become available.

> **NOTE**
>
> In call scenarios, if a Bluetooth or NearLink device is online, the system uses the Bluetooth or NearLink device as the input device by default.

```ts
import { audio } from '@kit.AudioKit';  // Import the audio module.
import { BusinessError } from '@kit.BasicServicesKit';

let audioManager = audio.getAudioManager();  // Create an AudioManager instance.

let audioSessionManager = audioManager.getSessionManager();  // Call an API of AudioManager to create an AudioSessionManager instance.

audioSessionManager.setBluetoothAndNearlinkPreferredRecordCategory(audio.BluetoothAndNearlinkPreferredRecordCategory.PREFERRED_LOW_LATENCY).then(() => {
  console.info('Succeeded in setting bluetooth and nearlink preferred record category.');
}).catch((err: BusinessError) => {
  console.error(`Failed to set bluetooth and nearlink preferred record category. Code: ${err.code}, message: ${err.message}`);
});
```

## Manually Selecting Input Devices

Applications can use [selectMediaInputDevice](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#selectmediainputdevice21) of AudioSessionManager to select an input device.

> **NOTE**
>
> In call scenarios, the input device follows the current output device, and other concurrent recording streams also follows the call input device.

```ts
import { audio } from '@kit.AudioKit';  // Import the audio module.
import { BusinessError } from '@kit.BasicServicesKit';

let audioManager = audio.getAudioManager();  // Create an AudioManager instance.

let audioSessionManager = audioManager.getSessionManager();  // Call an API of AudioManager to create an AudioSessionManager instance.

// When an input device goes online or offline, a callback notification is received. Listen for changes in the connection status of available audio input devices.
let availableDeviceChangeCallback = (deviceChanged: audio.DeviceChangeAction) => {
  // The callback returns the updated list of available input devices, and the application can also select an input device here.
  let data: audio.AudioDeviceDescriptors = deviceChanged.deviceDescriptors;
  console.info(`Succeeded in using on or off function, AudioDeviceDescriptors: ${data}.`);
};
audioSessionManager.on('availableDeviceChange', audio.DeviceUsage.MEDIA_INPUT_DEVICES, availableDeviceChangeCallback);

// Listen for changes in the current input device. The callback is triggered when an input device is selected.
let currentInputDeviceChangedCallback = (currentInputDeviceChangedEvent: audio.CurrentInputDeviceChangedEvent) => {
  console.info(`Succeeded in using on or off function, CurrentInputDeviceChangedEvent: ${currentInputDeviceChangedEvent}.`);
};
audioSessionManager.on('currentInputDeviceChanged', currentInputDeviceChangedCallback);

try {
  // Obtain the list of currently available audio input devices.
  let data: audio.AudioDeviceDescriptors = audioSessionManager.getAvailableDevices(audio.DeviceUsage.MEDIA_INPUT_DEVICES);
  console.info(`Succeeded in getting available devices, AudioDeviceDescriptors: ${data}.`);

  // If the list of currently available audio input devices is not empty, you can make a selection.
  if (data[0]) {
    // Select an input device.
    await audioSessionManager.selectMediaInputDevice(data[0]).then(() => {
      console.info('Succeeded in selecting media input device.');
    }).catch((err: BusinessError) => {
      console.error(`Failed to select media input device. Code: ${err.code}, message: ${err.message}`);
    });
  }
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get available devices. Code: ${error.code}, message: ${error.message}`);
}

// Check whether the input device selection is successful.
try {
  let device: audio.AudioDeviceDescriptor = audioSessionManager.getSelectedMediaInputDevice();
  console.info('Succeeded in getting select media input device.');
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get selected media input device. Code: ${error.code}, message: ${error.message}`);
}

// Stop listening for changes in the connection status of available audio input devices.
audioSessionManager.off('availableDeviceChange', availableDeviceChangeCallback);

// Stop listening for changes in the current input device.
audioSessionManager.off('currentInputDeviceChanged', currentInputDeviceChangedCallback);

// Clear the input device selected via selectMediaInputDevice.
audioSessionManager.clearSelectedMediaInputDevice().then(() => {
  console.info('Succeeded in clearing selected media input device.');
}).catch((err: BusinessError) => {
  console.error(`Failed to clear selected media input device. Code: ${err.code}, message: ${err.message}`);
});
```
