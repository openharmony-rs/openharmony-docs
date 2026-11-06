# Interface (AudioSessionManager)
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @LauJianghu-->
<!--Designer: @hao-liangfei-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=625af9d3f0edd94bf32a555a009e14a9b39281f8 translatedAt=2026-11-03T03:38:21.565Z pushedAt=2026-11-04T03:11:46.925Z nl=1 -->

AudioSessionManager is the session management module in the audio system. This module provides audio session management capabilities, including activation and deactivation of audio sessions, audio focus control, audio device selection and switching, and audio scene setting. When developers need to coordinate the audio playback behavior of multiple applications and resolve audio focus conflicts, they can use the APIs of this module to complete related operations. It is applicable to scenarios such as media playback, VoIP calls, and games that require fine-grained audio management.

Before calling any API in AudioSessionManager, you must use [getSessionManager](arkts-apis-audio-AudioManager.md#getsessionmanager12) to obtain an AudioSessionManager instance.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The initial APIs of this interface are supported since API version 12.

## Modules to Import

```ts
import { audio } from '@kit.AudioKit';
```

## activateAudioSession<sup>12+</sup>

activateAudioSession(strategy: AudioSessionStrategy): Promise\<void>

Activates an audio session. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Parameters**

| Name| Type                                             | Mandatory| Description        |
| ------ |-------------------------------------------------| ---- | ------------ |
| strategy | [AudioSessionStrategy](arkts-apis-audio-i.md#audiosessionstrategy12) | Yes  | Audio session strategy.|

**Return value**

| Type          | Description                     |
| -------------- | ------------------------- |
| Promise\<void> | Promise object, no return result. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | ---------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters unspecified. 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed.|
| 6800301 | System error. Possible causes: 1.Focus preemption failure. 2.Audio server process died. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// Set the audio session concurrency mode to mixing mode.
let strategy: audio.AudioSessionStrategy = {
  concurrencyMode: audio.AudioConcurrencyMode.CONCURRENCY_MIX_WITH_OTHERS
};

audioSessionManager.activateAudioSession(strategy).then(() => {
  console.info('Succeeded in activating the audio session.');
}).catch((err: BusinessError) => {
  console.error(`Failed to activate the audio session. Code: ${err.code}, message: ${err.message}`);
});
```

## deactivateAudioSession<sup>12+</sup>

deactivateAudioSession(): Promise\<void>

Deactivates this audio session. This API uses a promise to return the result.

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Return value**

| Type          | Description                     |
| -------------- | ------------------------- |
| Promise\<void> | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | ---------------------------------------------|
| 6800301 | System error. Possible causes: 1.The audio session does not exist or has been released. 2.Audio server process died. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioSessionManager.deactivateAudioSession().then(() => {
  console.info('Succeeded in deactivating the audio session.');
}).catch((err: BusinessError) => {
  console.error(`Failed to deactivate the audio session. Code: ${err.code}, message: ${err.message}`);
});
```

## isAudioSessionActivated<sup>12+</sup>

isAudioSessionActivated(): boolean

Checks whether this audio session is activated.

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Return value**

| Type                                             | Description                                   |
| ------------------------------------------------- |---------------------------------------|
| boolean | Check result for whether the audio session is activated. **true** if activated, **false** otherwise.|

**Example**

```ts
let isActivated = audioSessionManager.isAudioSessionActivated();
```

## on('audioSessionDeactivated')<sup>12+</sup>

on(type: 'audioSessionDeactivated', callback: Callback\<AudioSessionDeactivatedEvent>): void

Subscribes to the audio session deactivation event, which is triggered when an audio session is deactivated. This API uses an asynchronous callback to return the result.

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Parameters**

| Name  | Type                                                                       | Mandatory| Description                                                        |
| -------- |---------------------------------------------------------------------------| ---- | ------------------------------------------------------------ |
| type     | string | Yes  | Event type. The event **'audioSessionDeactivated'** is triggered when the audio session is deactivated.|
| callback | Callback<[AudioSessionDeactivatedEvent](arkts-apis-audio-i.md#audiosessiondeactivatedevent12)> | Yes  | Callback used to return the reason why the audio session is deactivated.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters unspecified. 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**Example**

```ts
audioSessionManager.on('audioSessionDeactivated',
  (audioSessionDeactivatedEvent: audio.AudioSessionDeactivatedEvent) => {
  console.info(`Audio session deactivated, audioSessionDeactivatedEvent: ${JSON.stringify(audioSessionDeactivatedEvent)}.`);
});
```

## off('audioSessionDeactivated')<sup>12+</sup>

off(type: 'audioSessionDeactivated', callback?: Callback\<AudioSessionDeactivatedEvent>): void

Unregisters the listener for the audio session deactivation event.

**Atomic service API**: This API can be used in atomic services since API version 26.0.0.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Parameters**

| Name  | Type                                  | Mandatory| Description                                                        |
| -------- | -------------------------------------- | ---- | ------------------------------------------------------------ |
| type     | string | Yes  | Event callback type. The supported event is 'audioSessionDeactivated'. |
| callback |Callback<[AudioSessionDeactivatedEvent](arkts-apis-audio-i.md#audiosessiondeactivatedevent12)> | No  | Callback for the event. When a callback is passed in, only the listening event corresponding to this callback is unregistered, and it must be bound to the same callback as [on('audioSessionDeactivated')](#onaudiosessiondeactivated12). When no parameter is passed in, all subscribed listening events of this event type are unregistered. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**Example**

```ts
// Cancel all subscriptions to the event.
audioSessionManager.off('audioSessionDeactivated');

// For the same event, if the callback parameter passed to the off API is the same as that passed to the on API, the off API cancels the subscription registered with the specified callback parameter.
let audioSessionDeactivatedCallback = (audioSessionDeactivatedEvent: audio.AudioSessionDeactivatedEvent) => {
  console.info(`Audio session deactivated, audioSessionDeactivatedEvent: ${JSON.stringify(audioSessionDeactivatedEvent)}.`);
};

audioSessionManager.on('audioSessionDeactivated', audioSessionDeactivatedCallback);

audioSessionManager.off('audioSessionDeactivated', audioSessionDeactivatedCallback);
```

## setAudioSessionScene<sup>20+</sup>

setAudioSessionScene(scene: AudioSessionScene): void

Sets an audio session scene.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Parameters**

| Name  | Type                                  | Mandatory| Description                                                        |
| -------- | -------------------------------------- | ---- | ------------------------------------------------------------ |
| scene     | [AudioSessionScene](arkts-apis-audio-e.md#audiosessionscene20) | Yes  | Audio session scene.|

**Error codes**

For details about the error codes, see [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | ---------------------------------------------|
| 6800101 | Parameter verification failed. |
| 6800103 | Operation not permitted at current state.|
| 6800301 | Audio client call audio service error, System error. |

**Example**

```ts
audioSessionManager.setAudioSessionScene(audio.AudioSessionScene.AUDIO_SESSION_SCENE_MEDIA);
```

## on('audioSessionStateChanged')<sup>20+</sup>

on(type: 'audioSessionStateChanged', callback: Callback\<AudioSessionStateChangedEvent>): void

Subscribes to the audio session state change event, which is triggered when the audio session focus is changed. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Parameters**

| Name  | Type                                                                       | Mandatory| Description                                                        |
| -------- |---------------------------------------------------------------------------| ---- | ------------------------------------------------------------ |
| type     | string | Yes  | Event type. The event **'audioSessionStateChanged'** is triggered when the audio session state is changed.|
| callback | Callback<[AudioSessionStateChangedEvent](arkts-apis-audio-i.md#audiosessionstatechangedevent20)> | Yes  | Callback used to return the audio session change information.|

**Error codes**

For details about the error codes, see [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 6800101 | Parameter verification failed. |
| 6800102 | Allocate memory failed. |
| 6800301 | Audio client call audio service error, System error. |

**Example**

```ts
audioSessionManager.on('audioSessionStateChanged', (audioSessionStateChangedEvent: audio.AudioSessionStateChangedEvent) => {
  console.info(`Audio session state changed, audioSessionStateChangedEvent: ${JSON.stringify(audioSessionStateChangedEvent)}.`);
});
```

## off('audioSessionStateChanged')<sup>20+</sup>

off(type: 'audioSessionStateChanged', callback?: Callback\<AudioSessionStateChangedEvent>): void

Unregisters the listener for the audio session state change event.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Parameters**

| Name  | Type                                                                       | Mandatory| Description                                                        |
| -------- |---------------------------------------------------------------------------| ---- | ------------------------------------------------------------ |
| type     | string | Yes   | Event callback type. The supported event is 'audioSessionStateChanged'. |
| callback | Callback<[AudioSessionStateChangedEvent](arkts-apis-audio-i.md#audiosessionstatechangedevent20)> | No | Callback function. When a callback function is passed in, only the listening event corresponding to this callback is unregistered, and the same callback function must be bound as in [on('audioSessionStateChanged')](#onaudiosessionstatechanged20). When no parameter is passed in, all subscribed listening events of this event type are unregistered. |

**Error codes**

For details about the error codes, see [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 6800101 | Parameter verification failed. |
| 6800301 | Audio client call audio service error, System error. |

**Example**

```ts
// Cancel all subscriptions to the event.
audioSessionManager.off('audioSessionStateChanged');

// For the same event, if the callback parameter passed to the off API is the same as that passed to the on API, the off API cancels the subscription registered with the specified callback parameter.
let audioSessionStateChangedCallback = (audioSessionStateChangedEvent: audio.AudioSessionStateChangedEvent) => {
  console.info(`Audio session state changed, audioSessionStateChangedEvent: ${JSON.stringify(audioSessionStateChangedEvent)}.`);
};

audioSessionManager.on('audioSessionStateChanged', audioSessionStateChangedCallback);

audioSessionManager.off('audioSessionStateChanged', audioSessionStateChangedCallback);
```

## setDefaultOutputDevice<sup>20+</sup>

setDefaultOutputDevice(deviceType: DeviceType): Promise&lt;void&gt;

Sets the default audio output device. This API uses a promise to return the result.

> **NOTE**
>
> - This API is applicable to the following situations: when the [AudioSessionScene](arkts-apis-audio-e.md#audiosessionscene20) is set to the VoIP or voice message scene, it takes effect immediately after the AudioSession is activated. If the [AudioSessionScene](arkts-apis-audio-e.md#audiosessionscene20) is set to another scene, it does not take effect when the AudioSession is activated, but only takes effect when the [StreamUsage](arkts-apis-audio-e.md#streamusage) of the started playback is voice message, VoIP voice call, or VoIP video call. The earpiece, speaker, and system default device are supported.
> - This API can be called at any time after the AudioSessionManager is created. The system records the default built-in sound-emitting device set by the application. However, it takes effect only after the AudioSession is activated. When the application starts playback, if an external device such as a Bluetooth headset or a wired headset is connected, the system gives priority to sound output from the external device. Otherwise, the system follows the default built-in sound-emitting device set by the application.
> - Because AudioSessionManager is an application-level setting, calling this API to set the default audio output device takes effect on all audio streams within the applicable scope of the current application, and overrides the default audio output device information set by the [setDefaultOutputDevice](../../reference/apis-audio-kit/arkts-apis-audio-AudioRenderer.md#setdefaultoutputdevice12) API of AudioRenderer.

**System capability**: SystemCapability.Multimedia.Audio.Device

**Device behavior difference**: If the default audio output device is set to earpiece on a device without a earpiece, the speaker will still be used for audio output.

**Parameters**

| Name    | Type            | Mandatory  | Description                                                     |
| ---------- |----------------| ------ |---------------------------------------------------------|
| deviceType | [DeviceType](arkts-apis-audio-e.md#devicetype) | Yes    | Device type.<br>The options are **EARPIECE**, **SPEAKER**, and **DEFAULT**.|

**Return value**

| Type               | Description                         |
| ------------------- | ----------------------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 6800101 | Parameter verification failed. Return by promise. |
| 6800102 | Allocate memory failed. Return by promise. |
| 6800301 | Audio client call audio service error, System error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioSessionManager.setDefaultOutputDevice(audio.DeviceType.SPEAKER).then(() => {
  console.info('Succeeded in setting the default output device.');
}).catch((err: BusinessError) => {
  console.error(`Failed to set the default output device. Code: ${err.code}, message: ${err.message}`);
});
```

## getDefaultOutputDevice<sup>20+</sup>

getDefaultOutputDevice(): DeviceType

Obtains the default audio output device set by calling [setDefaultOutputDevice](#setdefaultoutputdevice20).

**System capability**: SystemCapability.Multimedia.Audio.Device

**Return value**

| Type                                             | Description                                   |
| ------------------------------------------------- |---------------------------------------|
| DeviceType |Device type.<br>The options are **EARPIECE**, **SPEAKER**, and **DEFAULT**.|

**Error codes**

For details about the error codes, see [Audio Error Codes](errorcode-audio.md).

| ID  | Error Message|
|---------| --------------------------------------------|
| 6800101 | Parameter verification failed. |
| 6800103 | Operation not permitted at current state. Return by promise. |

**Example**

```ts
let deviceType = audioSessionManager.getDefaultOutputDevice();
```

## setMediaOutputDevice

setMediaOutputDevice(deviceType: DeviceType): Promise&lt;void&gt;

Switches the media output device to the built-in speaker when other external audio devices (such as Bluetooth headphones or wired headphones) are connected. This API uses a promise to return the result.

> **NOTE**
>
> - This API is applicable only to the media playback scenario, and it takes effect on all media streams initiated within the application.
> - If there is a concurrent playback stream with a higher priority or the user manually selects an output device, the output device actually used by the application will differ from the device set by this API. The application can listen for the [CurrentOutputDeviceChangedEvent](arkts-apis-audio-i.md#currentoutputdevicechangedevent20) event to obtain the currently active output device.
> - When the application needs to clear the speaker output configuration previously set through the API, it can call the API to set the media output device to DEFAULT (system default device). This setting is valid only while the application is running. When the application exits, the setting made by this API is automatically cleared.

**Since**: 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Device

**Device behavior differences:** When this API sets the output device to speaker on a device without a speaker, the setting does not take effect.

**Parameters**

| Name     | Type             | Mandatory   | Description                                                      |
| ---------- |----------------| ------ |---------------------------------------------------------|
| deviceType | [DeviceType](arkts-apis-audio-e.md#devicetype) | Yes     | Device type.<br>Only the following devices are supported: SPEAKER and DEFAULT (system default device). |

**Return value**

| Type                | Description                          |
| ------------------- | ----------------------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Audio Error Codes](errorcode-audio.md).

| ID | Error Message |
| ------- | --------------------------------------------|
| 6800101 | Parameter verification failed, for example, the selected device type is not supported. |
| 6800301 | System error. Possible causes: 1. Internal variable memory allocation failed. 2. Audio server process died. 3. Speaker device is not available. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioSessionManager.setMediaOutputDevice(audio.DeviceType.SPEAKER).then(() => {
  console.info('Succeeded in setting the media output device.');
}).catch((err: BusinessError) => {
  console.error(`Failed to set the media output device. Code: ${err.code}, message: ${err.message}`);
});
```

## on('currentOutputDeviceChanged')<sup>20+</sup>

on(type: 'currentOutputDeviceChanged', callback: Callback\<CurrentOutputDeviceChangedEvent>): void

Subscribes to the current output device change event, which is triggered when the current output device is changed. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.Audio.Device

**Parameters**

| Name  | Type                                                | Mandatory| Description                                                     |
| :------- | :--------------------------------------------------- | :--- |:--------------------------------------------------------|
| type     | string | Yes  | Event type. The event **'currentOutputDeviceChanged'** is triggered when the current output device is changed.|
| callback | Callback<[CurrentOutputDeviceChangedEvent](arkts-apis-audio-i.md#currentoutputdevicechangedevent20)> | Yes  | Callback used to return the information about the current output device.|

**Error codes**

For details about the error codes, see [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 6800101 | Parameter verification failed. |
| 6800102 | Allocate memory failed. |
| 6800301 | Audio client call audio service error, System error. |

**Example**

```ts
let currentOutputDeviceChangedCallback = (currentOutputDeviceChangedEvent: audio.CurrentOutputDeviceChangedEvent) => {
  console.info(`Current output device changed, currentOutputDeviceChangedEvent: ${JSON.stringify(currentOutputDeviceChangedEvent)}.`);
};

audioSessionManager.on('currentOutputDeviceChanged', currentOutputDeviceChangedCallback);
```

## off('currentOutputDeviceChanged')<sup>20+</sup>

off(type: 'currentOutputDeviceChanged', callback?: Callback\<CurrentOutputDeviceChangedEvent>): void

Unregisters the listener for the current output device change event.

**System capability**: SystemCapability.Multimedia.Audio.Device

**Parameters**

| Name  | Type                                                | Mandatory| Description                                                     |
| :------- | :--------------------------------------------------- | :--- |:--------------------------------------------------------|
| type     | string | Yes  | Event callback type. The supported event is 'currentOutputDeviceChanged'. |
| callback | Callback<[CurrentOutputDeviceChangedEvent](arkts-apis-audio-i.md#currentoutputdevicechangedevent20)> | No | Callback function. When a callback function is passed in, only the listening event corresponding to this callback is unregistered, and the same callback function must be bound as in [on('currentOutputDeviceChanged')](#oncurrentoutputdevicechanged20). When no parameter is passed, all subscribed listening events of this event type are unregistered. |

**Error codes**

For details about the error codes, see [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 6800101 | Parameter verification failed. |
| 6800301 | Audio client call audio service error, System error. |

**Example**

```ts
// Cancel all subscriptions to the event.
audioSessionManager.off('currentOutputDeviceChanged');

// For the same event, if the callback parameter passed to the off API is the same as that passed to the on API, the off API cancels the subscription registered with the specified callback parameter.
let currentOutputDeviceChangedCallback = (currentOutputDeviceChangedEvent: audio.CurrentOutputDeviceChangedEvent) => {
  console.info(`Current output device changed, currentOutputDeviceChangedEvent: ${JSON.stringify(currentOutputDeviceChangedEvent)}.`);
};

audioSessionManager.on('currentOutputDeviceChanged', currentOutputDeviceChangedCallback);

audioSessionManager.off('currentOutputDeviceChanged', currentOutputDeviceChangedCallback);
```

## getAvailableDevices<sup>21+</sup>

getAvailableDevices(deviceUsage: DeviceUsage): AudioDeviceDescriptors

Obtains the available audio devices.

**System capability**: SystemCapability.Multimedia.Audio.Device

**Parameters**

| Name  | Type                                                | Mandatory| Description                                                     |
| :------- | :--------------------------------------------------- | :--- |:--------------------------------------------------------|
| deviceUsage| [DeviceUsage](arkts-apis-audio-e.md#deviceusage12) | Yes  | Audio device type (classified by usage).|

**Return value**

| Type                                                        | Description                     |
| ------------------------------------------------------------ | ------------------------- |
| [AudioDeviceDescriptors](arkts-apis-audio-t.md#audiodevicedescriptors) | Device list.|

**Error codes**

For details about the error codes, see [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 6800101 | Parameter verification failed. |
| 6800301 | Audio client call audio service error, System error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data: audio.AudioDeviceDescriptors = audioSessionManager.getAvailableDevices(audio.DeviceUsage.MEDIA_OUTPUT_DEVICES);
  console.info(`Succeeded in obtaining available devices, audioDeviceDescriptors: ${JSON.stringify(data)}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to obtain available devices. Code: ${error.code}, message: ${error.message}`);
}
```

## on('availableDeviceChange')<sup>21+</sup>

on(type: 'availableDeviceChange', deviceUsage: DeviceUsage, callback: Callback\<DeviceChangeAction>): void

Subscribes to the event indicating that the connection status of an available audio device is changed.

**System capability**: SystemCapability.Multimedia.Audio.Device

**Parameters**

| Name  | Type                                                | Mandatory| Description                                                     |
| :------- | :--------------------------------------------------- | :--- |:--------------------------------------------------------|
| type     | string                                               | Yes  | Event type. The event **'availableDeviceChange'** is triggered when the connection status of available audio devices is changed.|
| deviceUsage | [DeviceUsage](arkts-apis-audio-e.md#deviceusage12)                       | Yes  | Audio device type (classified by usage).    |
| callback | Callback<[DeviceChangeAction](arkts-apis-audio-i.md#devicechangeaction)\> | Yes  | Callback used to return the available device change details.|

**Error codes**

For details about the error codes, see [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 6800101 | Parameter verification failed. |
| 6800301 | Audio client call audio service error, System error. |

**Example**

```ts
audioSessionManager.on('availableDeviceChange', audio.DeviceUsage.MEDIA_INPUT_DEVICES, (deviceChanged: audio.DeviceChangeAction) => {
  console.info(`Available device changed, deviceChangeAction: ${JSON.stringify(deviceChanged)}.`);
});
```

## off('availableDeviceChange')<sup>21+</sup>

off(type: 'availableDeviceChange', callback?: Callback<DeviceChangeAction\>): void

Unsubscribes from the event indicating that the connection status of an available audio device is changed.

**System capability**: SystemCapability.Multimedia.Audio.Device

**Parameters**

| Name  | Type                                               | Mandatory| Description                                      |
| -------- | --------------------------------------------------- | ---- | ------------------------------------------ |
| type     | string | Yes   | Event callback type. The supported event is 'availableDeviceChange'. |
| callback | Callback\<[DeviceChangeAction](arkts-apis-audio-i.md#devicechangeaction)\> | No   | Callback function. When a callback function is passed in, only the listening event corresponding to this callback is unregistered, and it must be bound to the same callback function as [on('availableDeviceChange')](#onavailabledevicechange21); when no parameter is passed, all subscribed listening events of this event type are unregistered. |

**Error codes**

For details about the error codes, see [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 6800301 | Audio client call audio service error, System error. |

**Example**

```ts
// Cancel all subscriptions to the event.
audioSessionManager.off('availableDeviceChange');

// For the same event, if the callback parameter passed to the off API is the same as that passed to the on API, the off API cancels the subscription registered with the specified callback parameter.
let availableDeviceChangeCallback = (deviceChanged: audio.DeviceChangeAction) => {
  console.info(`Available device changed, deviceChangeAction: ${JSON.stringify(deviceChanged)}.`);
};

audioSessionManager.on('availableDeviceChange', audio.DeviceUsage.MEDIA_INPUT_DEVICES, availableDeviceChangeCallback);

audioSessionManager.off('availableDeviceChange', availableDeviceChangeCallback);
```

## selectMediaInputDevice<sup>21+</sup>

selectMediaInputDevice(inputAudioDevice: AudioDeviceDescriptor): Promise<void\>

Selects a media input device. This API uses a promise to return the result.

> **NOTE**
>
> - This API is not applicable to VoIP call recording, that is, it is not applicable to the scenario where [SourceType](arkts-apis-audio-e.md#sourcetype8) is SOURCE_TYPE_VOICE_COMMUNICATION.
> - Before calling this API, call [getAvailableDevices](#getavailabledevices21) to query the list of currently available input devices, and select an input device from the list.
> - When there is a recording stream of another application with a higher priority in the system, the input device actually used follows the input device selected by the other higher-priority application.
> - The application can listen for the [currentInputDeviceChanged](#oncurrentinputdevicechanged21) event to obtain the actual input device.

**System capability**: SystemCapability.Multimedia.Audio.Device

**Parameters**

| Name  | Type                                                | Mandatory| Description                                                     |
| :------- | :--------------------------------------------------- | :--- |:--------------------------------------------------------|
| inputAudioDevice| [AudioDeviceDescriptor](arkts-apis-audio-i.md#audiodevicedescriptor) | Yes  | Media input device.|

**Return value**

| Type          | Description                     |
| -------------- | ------------------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 6800101 | Parameter verification failed, for example, the selected device does not exist. |
| 6800301 | Audio client call audio service error, System error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // Obtain the list of available audio input devices for subsequent selection of an input device.
  let data: audio.AudioDeviceDescriptors = audioSessionManager.getAvailableDevices(audio.DeviceUsage.MEDIA_INPUT_DEVICES);
  console.info(`Succeeded in obtaining available devices, audioDeviceDescriptors: ${JSON.stringify(data)}.`);

  if (data[0]) {
    // Select the first available device as the audio input device.
    audioSessionManager.selectMediaInputDevice(data[0]).then(() => {
      console.info('Succeeded in selecting the media input device.');
    }).catch((selectErr: BusinessError) => {
      console.error(`Failed to select the media input device. Code: ${selectErr.code}, message: ${selectErr.message}`);
    });
  }
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to obtain available devices. Code: ${error.code}, message: ${error.message}`);
}
```

## getSelectedMediaInputDevice<sup>21+</sup>

getSelectedMediaInputDevice(): AudioDeviceDescriptor

Obtains the media input device set by calling [selectMediaInputDevice](#selectmediainputdevice21). If no device has been specified, the device with **deviceType** set to **INVALID** is returned.

**System capability**: SystemCapability.Multimedia.Audio.Device

**Return value**

| Type          | Description                     |
| -------------- | ------------------------- |
| [AudioDeviceDescriptor](arkts-apis-audio-i.md#audiodevicedescriptor) | Media input device.|

**Error codes**

For details about the error codes, see [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 6800301 | Audio client call audio service error, System error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let device: audio.AudioDeviceDescriptor = audioSessionManager.getSelectedMediaInputDevice();
  console.info(`Succeeded in obtaining the selected media input device, audioDeviceDescriptor: ${JSON.stringify(device)}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to obtain the selected media input device. Code: ${error.code}, message: ${error.message}`);
}
```

## clearSelectedMediaInputDevice<sup>21+</sup>

clearSelectedMediaInputDevice(): Promise<void\>

Clears the media input device set by calling [selectMediaInputDevice](#selectmediainputdevice21). This API uses a promise to return the result.

**System capability**: SystemCapability.Multimedia.Audio.Device

**Return value**

| Type          | Description                     |
| -------------- | ------------------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 6800301 | Audio client call audio service error, System error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioSessionManager.clearSelectedMediaInputDevice().then(() => {
  console.info('Succeeded in clearing the selected media input device.');
}).catch((err: BusinessError) => {
  console.error(`Failed to clear the selected media input device. Code: ${err.code}, message: ${err.message}`);
});
```

## setBluetoothAndNearlinkPreferredRecordCategory<sup>21+</sup>

setBluetoothAndNearlinkPreferredRecordCategory(category: BluetoothAndNearlinkPreferredRecordCategory): Promise<void\>

Sets the device preference category of the application when recording with Bluetooth or NearLink. This API uses a promise to return the result.

> **NOTE**
>
> - The application can set this category before Bluetooth or NearLink is connected, and the system will give priority to recording with Bluetooth or NearLink when the device is connected.
> - When there is a recording stream of another application with a higher priority in the system, the input device actually used follows the input device selected by the other higher-priority application.
> - The application can listen for the [currentInputDeviceChanged](#oncurrentinputdevicechanged21) event to obtain the actual input device.

**System capability**: SystemCapability.Multimedia.Audio.Device

**Parameters**

| Name  | Type                                                | Mandatory| Description                                                     |
| :------- | :--------------------------------------------------- | :--- |:--------------------------------------------------------|
| category| [BluetoothAndNearlinkPreferredRecordCategory](arkts-apis-audio-e.md#bluetoothandnearlinkpreferredrecordcategory21) | Yes   | Device preference category of the application when recording with Bluetooth or NearLink. |

**Return value**

| Type          | Description                     |
| -------------- | ------------------------- |
| Promise\<void> | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 6800101 | Parameter verification failed. |
| 6800301 | Audio client call audio service error, System error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// Set the Bluetooth and NearLink recording preference to low-latency mode, prioritizing low-latency devices.
let category = audio.BluetoothAndNearlinkPreferredRecordCategory.PREFERRED_LOW_LATENCY;

audioSessionManager.setBluetoothAndNearlinkPreferredRecordCategory(category).then(() => {
  console.info('Succeeded in setting the bluetooth and nearlink preferred record category.');
}).catch((err: BusinessError) => {
  console.error(`Failed to set the bluetooth and nearlink preferred record category. Code: ${err.code}, message: ${err.message}`);
});
```

## getBluetoothAndNearlinkPreferredRecordCategory<sup>21+</sup>

getBluetoothAndNearlinkPreferredRecordCategory(): BluetoothAndNearlinkPreferredRecordCategory

Obtains the preferred device category for recording with Bluetooth or NearLink, which is set by calling [setBluetoothAndNearlinkPreferredRecordCategory](#setbluetoothandnearlinkpreferredrecordcategory21).

**System capability**: SystemCapability.Multimedia.Audio.Device

**Return value**

| Type          | Description                     |
| -------------- | ------------------------- |
| [BluetoothAndNearlinkPreferredRecordCategory](arkts-apis-audio-e.md#bluetoothandnearlinkpreferredrecordcategory21) | Returns the currently set Bluetooth or NearLink recording device preference category. |

**Error codes**

For details about the error codes, see [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 6800301 | Audio client call audio service error, System error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let category: audio.BluetoothAndNearlinkPreferredRecordCategory = audioSessionManager.getBluetoothAndNearlinkPreferredRecordCategory();
  console.info(`Succeeded in obtaining the bluetooth and nearlink preferred record category, category: ${category}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to obtain the bluetooth and nearlink preferred record category. Code: ${error.code}, message: ${error.message}`);
}
```

## on('currentInputDeviceChanged')<sup>21+</sup>

on(type: 'currentInputDeviceChanged', callback: Callback<CurrentInputDeviceChangedEvent\>): void

Subscribes to the current input device change event, which is triggered when the current input device is changed.

**System capability**: SystemCapability.Multimedia.Audio.Device

**Parameters**

| Name  | Type                                                | Mandatory| Description                                      |
| :------- | :--------------------------------------------------- | :--- | :----------------------------------------- |
| type     | string | Yes  | Event type. The event **'currentInputDeviceChanged'** is triggered when the current input device is changed.|
| callback | Callback\<[CurrentInputDeviceChangedEvent](arkts-apis-audio-i.md#currentinputdevicechangedevent21)\> | Yes  | Callback used to return the information about the current input device.|

**Error codes**

For details about the error codes, see [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 6800101 | Parameter verification failed. |
| 6800301 | Audio client call audio service error, System error. |

**Example**

```ts
let currentInputDeviceChangedCallback = (currentInputDeviceChangedEvent: audio.CurrentInputDeviceChangedEvent) => {
  console.info(`Current input device changed, currentInputDeviceChangedEvent: ${JSON.stringify(currentInputDeviceChangedEvent)}.`);
};

audioSessionManager.on('currentInputDeviceChanged', currentInputDeviceChangedCallback);
```

## off('currentInputDeviceChanged')<sup>21+</sup>

off(type: 'currentInputDeviceChanged', callback?: Callback<CurrentInputDeviceChangedEvent\>): void

Unsubscribes from the current input device change event.

**System capability**: SystemCapability.Multimedia.Audio.Device

**Parameters**

| Name  | Type                                                | Mandatory| Description                                                     |
| :------- | :--------------------------------------------------- | :--- |:--------------------------------------------------------|
| type     | string | Yes  | Event callback type. The supported event is 'currentInputDeviceChanged'. |
| callback | Callback<[CurrentInputDeviceChangedEvent](arkts-apis-audio-i.md#currentinputdevicechangedevent21)> | No | Callback function. When a callback function is passed in, only the listening event corresponding to this callback is unregistered, and the same callback function must be bound as in [on('currentInputDeviceChanged')](#oncurrentinputdevicechanged21); when no parameter is passed in, all listening events subscribed under this event type are unregistered. |

**Error codes**

For details about the error codes, see [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 6800301 | Audio client call audio service error, System error. |

**Example**

```ts
// Cancel all subscriptions to the event.
audioSessionManager.off('currentInputDeviceChanged');

// For the same event, if the callback parameter passed to the off API is the same as that passed to the on API, the off API cancels the subscription registered with the specified callback parameter.
let currentInputDeviceChangedCallback = (currentInputDeviceChangedEvent: audio.CurrentInputDeviceChangedEvent) => {
  console.info(`Current input device changed, currentInputDeviceChangedEvent: ${JSON.stringify(currentInputDeviceChangedEvent)}.`);
};

audioSessionManager.on('currentInputDeviceChanged', currentInputDeviceChangedCallback);

audioSessionManager.off('currentInputDeviceChanged', currentInputDeviceChangedCallback);
```

## enableMuteSuggestionWhenMixWithOthers<sup>23+</sup>

enableMuteSuggestionWhenMixWithOthers(enable: boolean): void

Enables mute suggestion notifications for mixed playback.

Typically, when the audio mixing mode is used, if two applications plays audio at the same time, their audio streams are mixed. In certain scenarios (such as games or broadcasts), applications can mute their own audio to provide a better user experience.

If this feature is enabled, after subscribing to the audio session state change event, the mute suggestion and unmute suggestion prompts are sent through the [AudioSessionStateChangedEvent](arkts-apis-audio-i.md#audiosessionstatechangedevent20) callback. Receiving a mute suggestion indicates that another application has started playing audio, and the played audio cannot be mixed with the audio of this application.

This feature is supported only for audio sessions that have [AudioSessionScene](./arkts-apis-audio-e.md#audiosessionscene20) set and are activated in CONCURRENCY_MIX_WITH_OTHERS mode. It takes effect only once during the activation of an audio session, and must be re-enabled before each activation of the audio session.

For details, see [Enabling Mute Suggestion Notifications for Mixed Playback](../../media/audio/audio-session-management.md#enabling-mute-suggestion-notifications-for-mixed-playback).

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Parameters**

| Name  | Type              | Mandatory| Description     |
| -------- | ----------------- | ---- | --------- |
| enable   | boolean           | Yes   | Whether to enable the mute playback suggestion notification feature during mixed playback. The value true means to enable it, and false means the opposite. |

**Error codes**

For details about the error codes, see [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | ---------------------------------------------|
| 6800103 | Function is called without setting [AudioSessionScene](./arkts-apis-audio-e.md#audiosessionscene20) or called after audio session activation.|
| 6800301 | Audio client call audio service error, system internal error. |

**Example**

```ts
audioSessionManager.enableMuteSuggestionWhenMixWithOthers(true);
```


## setCapturerMuteHint<sup>24+</sup>

setCapturerMuteHint(mute: boolean): Promise&lt;void&gt;

Reports the mute state of the recording streams within the current audio session to the system audio module. <!--RP1-->This API does not trigger muting of recording streams, and is currently used only on certain PC/2-in-1 devices to optimize device power consumption. <!--RP1End-->This API uses a promise to return the result.

> **NOTE**
>
> - This API is used to report the mute state of the recording streams within the current audio session to the system audio module, and does not change the actual mute state of the recording streams.
> - This API can be called only when there is a running recording stream in the current audio session. Otherwise, error code 6800103 is returned.
> - If a recording stream has called both the stream-level API [AudioCapturer.setMuteHint](arkts-apis-audio-AudioCapturer.md#setmutehint24) and this API, the stream-level API takes precedence, and the value set by the stream-level API is used.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.Audio.Capturer

**Parameters**

| Name   | Type               | Mandatory | Description      |
| -------- | ----------------- | ---- | --------- |
| mute   | boolean           | Yes   | Mute state reported by the app to the system audio module. The value **true** indicates that the app mutes the current stream, and **false** indicates that muting is canceled. |

**Return value**

| Type           | Description                      |
| -------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Audio Error Codes](errorcode-audio.md).

| ID | Error Message |
| ------- | ---------------------------------------------|
| 6800103 | Operation not permitted at current state, there is no audio capturer running. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioSessionManager.setCapturerMuteHint(true).then(() => {
  console.info('Succeeded in setting the capturer mute hint.');
}).catch((err: BusinessError) => {
  console.error(`Failed to set the capturer mute hint. Code: ${err.code}, message: ${err.message}`);
});
```

## isOtherMediaPlaying<sup>23+</sup>

isOtherMediaPlaying(): boolean

Check whether any other application is currently playing audio of the four media types: **MUSIC**, **MOVIE**, **AUDIOBOOK**, and **GAME**. Audio sessions that have activated these media types will also be checked.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Return value**

| Type                                             | Description                                   |
| ------------------------------------------------- |---------------------------------------|
| boolean | Whether another application is playing audio of certain media types. **true** means yes; **false** otherwise.|

**Example**

```ts
let isExistence = audioSessionManager.isOtherMediaPlaying();
```

## setAudioSessionBehavior<sup>24+</sup>

setAudioSessionBehavior(behavior: number): void

Sets audio session behavior parameters. (Multiple flags can be combined.)

> **NOTE**
>
> If this API is called while the audio session is active, [activateAudioSession](#activateaudiosession12) must be called again for the change to take effect.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Parameters**

| Name  | Type              | Mandatory| Description     |
| -------- | ----------------- | ---- | --------- |
| behavior   | number           | Yes  | Specifies the audio session behavior.<br>This can be a single flag or a bitwise OR combination of multiple flags.<br>For details about the supported audio session behaviors, see [AudioSessionBehaviorFlags](./arkts-apis-audio-e.md#audiosessionbehaviorflags24).|

**Error codes**

For details about the error codes, see [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | ---------------------------------------------|
| 6800101 | Parameter verification failed. |
| 6800103 | Operation not permitted in the current state. |

**Example**

```ts
// Set the audio session behavior to mute when interrupted, so that the audio is automatically muted when interrupted by other applications.
let behavior: number = audio.AudioSessionBehaviorFlags.MUTE_WHEN_INTERRUPTED;
audioSessionManager.setAudioSessionBehavior(behavior);
```
