# Switching Audio Output Devices
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

When an application performs audio output, the system selects the corresponding output device based on the audio stream type. (If the audio stream type is **STREAM_USAGE_MUSIC**, the speaker is used. If the audio stream type is **STREAM_USAGE_VOICE_COMMUNICATION**, the earpiece is used.) If the default output device does not meet the application requirements, the application can use **AVCastPicker** or **setDefaultOutputDevice** to switch the audio output device.

## Switching Output Devices for Media Applications

Applications can use the [AVCastPicker](../../reference/apis-avsession-kit/ohos-multimedia-avcastpicker.md#avcastpicker) component to switch the output device for media applications.

## Switching Output Devices for Call Applications

### Switching External Devices

Call applications can use the [AVCastPicker](../avsession/using-switch-call-devices.md) component to switch the external output device.

### Switching Built-in Devices

In voice call scenarios, the system uses the earpiece for audio output by default. In other scenarios, the system defaults to using the speaker. (If an external device is connected, the system defaults to using the external device for audio output.)

To cancel the default output device set by calling **setDefaultOutputDevice**, you can set the parameter to **audio.DeviceType.DEFAULT**, which returns the audio output device selection to the system.

1. Applications can use [setDefaultOutputDevice](../../reference/apis-audio-kit/arkts-apis-audio-AudioRenderer.md#setdefaultoutputdevice12) of AudioRenderer to switch between the earpiece and speaker routing. Before calling this API, you need to obtain an [AudioRenderer](../../reference/apis-audio-kit/arkts-apis-audio-f.md#audiocreateaudiorenderer8) instance.

   > **NOTE**
   >
   > - AudioRenderer operates at the stream level. Therefore, the default audio output device set via this API take effect only for the current stream.
   > - This API has a lower priority than [setDefaultOutputDevice](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#setdefaultoutputdevice20) of AudioSessionManager. If [setDefaultOutputDevice](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#setdefaultoutputdevice20) of AudioSessionManager has been used to set the default audio output device, the settings made via this API does not take effect.

   ```ts
   import { audio } from '@kit.AudioKit';
   import { BusinessError } from '@kit.BasicServicesKit';

   // Set the default output device to the device speaker.
   audioRenderer.setDefaultOutputDevice(audio.DeviceType.SPEAKER).then(() => {
     console.info('Succeeded in setting default output device.');
   }).catch((err: BusinessError) => {
     console.error(`Failed to set default output device. Code: ${err.code}, message: ${err.message}`);
   });

   // Set the default output device to the default device, effectively canceling the application's default device setting.
   audioRenderer.setDefaultOutputDevice(audio.DeviceType.DEFAULT).then(() => {
     console.info('Succeeded in setting default output device.');
   }).catch((err: BusinessError) => {
     console.error(`Failed to set default output device. Code: ${err.code}, message: ${err.message}`);
   });
   ```

2. Applications can use [setDefaultOutputDevice](../../reference/apis-audio-kit/arkts-apis-audio-AudioSessionManager.md#setdefaultoutputdevice20) of AudioSessionManager to switch between the earpiece and speaker routing.

   > **NOTE**
   >
   > AudioSessionManager operates at the application level. Therefore, calling this API to set the default audio output device takes effect for all applicable audio streams within the current application and overrides the default audio output device settings made via [setDefaultOutputDevice](../../reference/apis-audio-kit/arkts-apis-audio-AudioRenderer.md#setdefaultoutputdevice12) of AudioRenderer.

   ```ts
   import { audio } from '@kit.AudioKit';  // Import the audio module.
   import { BusinessError } from '@kit.BasicServicesKit';

   let audioManager = audio.getAudioManager();  // Create an AudioManager instance.

   let audioSessionManager = audioManager.getSessionManager();  // Call an API of AudioManager to create an AudioSessionManager instance.

   // Set the default output device to the device speaker.
   audioSessionManager.setDefaultOutputDevice(audio.DeviceType.SPEAKER).then(() => {
     console.info('Succeeded in setting default output device.');
   }).catch((err: BusinessError) => {
     console.error(`Failed to set default output device. Code: ${err.code}, message: ${err.message}`);
   });

   // Set the default output device to the default device, effectively canceling the application's default device setting.
   audioSessionManager.setDefaultOutputDevice(audio.DeviceType.DEFAULT).then(() => {
     console.info('Succeeded in setting default output device.');
   }).catch((err: BusinessError) => {
     console.error(`Failed to set default output device. Code: ${err.code}, message: ${err.message}`);
   });
   ```
