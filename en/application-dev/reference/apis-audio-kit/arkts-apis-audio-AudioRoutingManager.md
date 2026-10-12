# Interface (AudioRoutingManager)
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @zhanganxiang1-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=59c3fabc0701f94b960b606856aa3cc084316830 translatedAt=2026-10-08T12:04:03.507Z pushedAt=2026-10-12T02:58:52.200Z -->

**AudioRoutingManager** is a device routing management module in the audio system. This module provides audio device routing management capabilities, including obtaining the audio device list, listening for device connection status changes, and obtaining the priority device. When you need to select an audio device route for media recording or playback, use the APIs provided by this module to complete related operations.

Before calling any API in AudioRoutingManager, you must use [getRoutingManager](arkts-apis-audio-AudioManager.md#getroutingmanager9) to obtain an AudioRoutingManager instance.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The initial APIs of this interface are supported since API version 9.

## Modules to Import

```ts
import { audio } from '@kit.AudioKit';
```

## getDevices<sup>9+</sup>

getDevices(deviceFlag: DeviceFlag, callback: AsyncCallback&lt;AudioDeviceDescriptors&gt;): void

Obtains the audio devices with a specific flag. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.Audio.Device

**Parameters**

| Name    | Type                                                        | Mandatory| Description                |
| ---------- | ------------------------------------------------------------ | ---- | -------------------- |
| deviceFlag | [DeviceFlag](arkts-apis-audio-e.md#deviceflag)                                    | Yes  | Audio device flag.    |
| callback   | AsyncCallback&lt;[AudioDeviceDescriptors](arkts-apis-audio-t.md#audiodevicedescriptors)&gt; | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the audio devices obtained; otherwise, **err** is an error object.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioRoutingManager.getDevices(audio.DeviceFlag.OUTPUT_DEVICES_FLAG, (err: BusinessError, audioDeviceDescriptors: audio.AudioDeviceDescriptors) => {
  if (err) {
    console.error(`Failed to obtain the device list. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in obtaining the device list, deviceDescriptors: ${JSON.stringify(audioDeviceDescriptors)}.`);
});
```

## getDevices<sup>9+</sup>

getDevices(deviceFlag: DeviceFlag): Promise&lt;AudioDeviceDescriptors&gt;

Obtains the audio devices with a specific flag. This API uses a promise to return the result.

**System capability**: SystemCapability.Multimedia.Audio.Device

**Parameters**

| Name    | Type                     | Mandatory| Description            |
| ---------- | ------------------------- | ---- | ---------------- |
| deviceFlag | [DeviceFlag](arkts-apis-audio-e.md#deviceflag) | Yes  | Audio device flag.|

**Return value**

| Type                                                        | Description                     |
| ------------------------------------------------------------ | ------------------------- |
| Promise&lt;[AudioDeviceDescriptors](arkts-apis-audio-t.md#audiodevicedescriptors)&gt; | Promise used to return the list of audio devices. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioRoutingManager.getDevices(audio.DeviceFlag.OUTPUT_DEVICES_FLAG).then((audioDeviceDescriptors: audio.AudioDeviceDescriptors) => {
  console.info(`Succeeded in obtaining the device list, deviceDescriptors: ${JSON.stringify(audioDeviceDescriptors)}.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to obtain the device list. Code: ${err.code}, message: ${err.message}`);
});
```

## getDevicesSync<sup>10+</sup>

getDevicesSync(deviceFlag: DeviceFlag): AudioDeviceDescriptors

Obtains the audio devices with a specific flag. This API returns the result synchronously.

**System capability**: SystemCapability.Multimedia.Audio.Device

**Parameters**

| Name    | Type                     | Mandatory| Description            |
| ---------- | ------------------------- | ---- | ---------------- |
| deviceFlag | [DeviceFlag](arkts-apis-audio-e.md#deviceflag) | Yes  | Audio device flag.|

**Return value**

| Type                                                        | Description                     |
| ------------------------------------------------------------ | ------------------------- |
| [AudioDeviceDescriptors](arkts-apis-audio-t.md#audiodevicedescriptors) | List of audio devices. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let audioDeviceDescriptors = audioRoutingManager.getDevicesSync(audio.DeviceFlag.OUTPUT_DEVICES_FLAG);
  console.info(`Succeeded in obtaining the device list, deviceDescriptors: ${JSON.stringify(audioDeviceDescriptors)}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to obtain the device list. Code: ${error.code}, message: ${error.message}`);
}
```

## isMicBlockDetectionSupported<sup>13+</sup>

isMicBlockDetectionSupported(): Promise&lt;boolean&gt;

Checks whether the current device supports microphone blocking detection. This API uses a promise to return the result.

**System capability**: SystemCapability.Multimedia.Audio.Device

**Return value**

| Type                  | Description                                                        |
| ---------------------- | ------------------------------------------------------------ |
| Promise&lt;boolean&gt; | Promise used to return the result, indicating the support for microphone blocking detection. **true** if supported, **false** otherwise.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioRoutingManager.isMicBlockDetectionSupported().then((value: boolean) => {
  console.info(`Succeeded in querying whether microphone block detection is supported, isSupported: ${value}.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to query whether microphone block detection is supported. Code: ${err.code}, message: ${err.message}`);
});
```

## on('micBlockStatusChanged')<sup>13+</sup>

on(type: 'micBlockStatusChanged', callback: Callback<DeviceBlockStatusInfo\>): void

Subscribes to the microphone blocked status change event. This API uses an asynchronous callback to return the result.

Before using this API, use [isMicBlockDetectionSupported](#ismicblockdetectionsupported13) to check whether the current device supports microphone blocking detection. This event is triggered when the microphone blocked status changes during recording. Currently, this API takes effect only for the microphone on the local device.

**System capability**: SystemCapability.Multimedia.Audio.Device

**Parameters**

| Name  | Type                                                | Mandatory| Description                                      |
| :------- | :--------------------------------------------------- | :--- | :----------------------------------------- |
| type     | string                                               | Yes  | Event type. The event **'micBlockStatusChanged'** is triggered when the microphone blocked status is changed.|
| callback | Callback<[DeviceBlockStatusInfo](arkts-apis-audio-i.md#deviceblockstatusinfo13)\> | Yes  | Callback used to return the microphone blocked status and device information.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**Example**

```ts
// Before the subscription, check whether the current device supports detection.
audioRoutingManager.isMicBlockDetectionSupported().then((value: boolean) => {
  console.info(`Succeeded in querying whether microphone block detection is supported, isSupported: ${value}.`);
  if (value) {
    audioRoutingManager.on('micBlockStatusChanged', (deviceBlockStatusInfo: audio.DeviceBlockStatusInfo) => {
      console.info(`MicBlockStatus changed, deviceBlockStatusInfo: ${JSON.stringify(deviceBlockStatusInfo)}.`);
    });
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to query whether microphone block detection is supported. Code: ${err.code}, message: ${err.message}`);
});
```

## off('micBlockStatusChanged')<sup>13+</sup>

off(type: 'micBlockStatusChanged', callback?: Callback<DeviceBlockStatusInfo\>): void

Unsubscribes from the microphone blocked status change event.

**System capability**: SystemCapability.Multimedia.Audio.Device

**Parameters**

| Name  | Type                                               | Mandatory| Description                                      |
| -------- | --------------------------------------------------- | ---- | ------------------------------------------ |
| type     | string                                              | Yes   | Event type. This field has a fixed value of **'micBlockStatusChanged'**. |
| callback | Callback<[DeviceBlockStatusInfo](arkts-apis-audio-i.md#deviceblockstatusinfo13)\> | No   | Callback used to return the result. If a callback is passed, only the listener for events corresponding to this callback will be unregistered. The callback must be the same as that bound to [on('micBlockStatusChanged')](#onmicblockstatuschanged13). If no parameter is passed, all listeners for events of this event type will be unregistered. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**Example**

```ts
// Cancel all subscriptions to the event.
audioRoutingManager.off('micBlockStatusChanged');

// For the same event, if the callback parameter passed to the off API is the same as that passed to the on API, the off API cancels the subscription registered with the specified callback parameter.
let micBlockStatusCallback = (deviceBlockStatusInfo: audio.DeviceBlockStatusInfo) => {
  console.info(`MicBlockStatus changed, deviceBlockStatusInfo: ${JSON.stringify(deviceBlockStatusInfo)}.`);
};

audioRoutingManager.on('micBlockStatusChanged', micBlockStatusCallback);

audioRoutingManager.off('micBlockStatusChanged', micBlockStatusCallback);
```

## on('deviceChange')<sup>9+</sup>

on(type: 'deviceChange', deviceFlag: DeviceFlag, callback: Callback<DeviceChangeAction\>): void

Subscribes to the event indicating that the connection status of an audio device is changed. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.Audio.Device

**Parameters**

| Name  | Type                                                | Mandatory| Description                     |
| :------- | :--------------------------------------------------- | :--- |:------------------------|
| type     | string                                               | Yes  | Event type. The event **'deviceChange'** is triggered when the connection status of an audio device is changed.|
| deviceFlag | [DeviceFlag](arkts-apis-audio-e.md#deviceflag)                                    | Yes  | Audio device flag.             |
| callback | Callback<[DeviceChangeAction](arkts-apis-audio-i.md#devicechangeaction)\> | Yes  | Callback used to return the device change details.         |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**Example**

```ts
audioRoutingManager.on('deviceChange', audio.DeviceFlag.OUTPUT_DEVICES_FLAG, (deviceChangeAction: audio.DeviceChangeAction) => {
  console.info(`Device changed, deviceChangeAction: ${JSON.stringify(deviceChangeAction)}.`);
});
```

## off('deviceChange')<sup>9+</sup>

off(type: 'deviceChange', callback?: Callback<DeviceChangeAction\>): void

Unsubscribes from the event indicating that the connection status of an audio device is changed.

**System capability**: SystemCapability.Multimedia.Audio.Device

**Parameters**

| Name  | Type                                               | Mandatory| Description                                      |
| -------- | --------------------------------------------------- | ---- | ------------------------------------------ |
| type     | string                                              | Yes   | Event type. This field has a fixed value of **'deviceChange'**. |
| callback | Callback<[DeviceChangeAction](arkts-apis-audio-i.md#devicechangeaction)> | No   | Callback used to return the result. If a callback is passed, only the listener for events corresponding to this callback will be unregistered. The callback must be the same as that bound to [on('deviceChange')](#ondevicechange9). If no parameter is passed, all listeners for events of this event type will be unregistered.  |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**Example**

```ts
// Cancel all subscriptions to the event.
audioRoutingManager.off('deviceChange');

// For the same event, if the callback parameter passed to the off API is the same as that passed to the on API, the off API cancels the subscription registered with the specified callback parameter.
let deviceChangeCallback = (deviceChangeAction: audio.DeviceChangeAction) => {
  console.info(`Device changed, deviceChangeAction: ${JSON.stringify(deviceChangeAction)}.`);
};

audioRoutingManager.on('deviceChange', audio.DeviceFlag.OUTPUT_DEVICES_FLAG, deviceChangeCallback);

audioRoutingManager.off('deviceChange', deviceChangeCallback);
```

## setCommunicationDevice<sup>9+</sup>

setCommunicationDevice(deviceType: CommunicationDeviceType, active: boolean, callback: AsyncCallback&lt;void&gt;): void

Sets a communication device to the active state. This API uses an asynchronous callback to return the result.

This API will be deprecated in a later version due to function design is changed. You are not advised to use it.

You are advised to use the [AVCastPicker component](../../media/avsession/using-switch-call-devices.md) provided by AVSession to switch between call devices.

**System capability**: SystemCapability.Multimedia.Audio.Communication

**Parameters**

| Name    | Type                                 | Mandatory| Description                     |
| ---------- | ------------------------------------- | ---- |-------------------------|
| deviceType | [CommunicationDeviceType](arkts-apis-audio-e.md#communicationdevicetype9) | Yes  | Audio device flag.                |
| active     | boolean                               | Yes  | Active state to set. **true** to set the device to the active state, **false** otherwise.|
| callback   | AsyncCallback&lt;void&gt;             | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioRoutingManager.setCommunicationDevice(audio.CommunicationDeviceType.SPEAKER, true, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to set the active status of the communication device. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in setting the active status of the communication device.');
});
```

## getAvailableDevices<sup>12+</sup>

getAvailableDevices(deviceUsage: DeviceUsage): AudioDeviceDescriptors

Obtains the available audio devices. This API returns the result synchronously.

**System capability**: SystemCapability.Multimedia.Audio.Device

**Parameters**

| Name    | Type                     | Mandatory| Description            |
| ---------- | ------------------------- | ---- | ---------------- |
| deviceUsage| [DeviceUsage](arkts-apis-audio-e.md#deviceusage12) | Yes  | Audio device type (classified by usage).|

**Return value**

| Type                                                        | Description                     |
| ------------------------------------------------------------ | ------------------------- |
| [AudioDeviceDescriptors](arkts-apis-audio-t.md#audiodevicedescriptors) | List of available audio devices. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data: audio.AudioDeviceDescriptors = audioRoutingManager.getAvailableDevices(audio.DeviceUsage.MEDIA_OUTPUT_DEVICES);
  console.info(`Succeeded in obtaining available devices, audioDeviceDescriptors: ${JSON.stringify(data)}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to obtain available devices. Code: ${error.code}, message: ${error.message}`);
}
```

## on('availableDeviceChange')<sup>12+</sup>

on(type: 'availableDeviceChange', deviceUsage: DeviceUsage, callback: Callback<DeviceChangeAction\>): void

Subscribes to the event indicating that the connection status of an available audio device is changed. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.Audio.Device

**Parameters**

| Name  | Type                                                | Mandatory| Description                                      |
| :------- | :--------------------------------------------------- | :--- | :----------------------------------------- |
| type     | string                                               | Yes  | Event type. The event **'availableDeviceChange'** is triggered when the connection status of available audio devices is changed.|
| deviceUsage | [DeviceUsage](arkts-apis-audio-e.md#deviceusage12)                       | Yes  | Audio device type (classified by usage).    |
| callback | Callback<[DeviceChangeAction](arkts-apis-audio-i.md#devicechangeaction)\> | Yes  | Callback used to return the device change details.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**Example**

```ts
audioRoutingManager.on('availableDeviceChange', audio.DeviceUsage.MEDIA_OUTPUT_DEVICES, (deviceChangeAction: audio.DeviceChangeAction) => {
  console.info(`Available device changed, deviceChangeAction: ${JSON.stringify(deviceChangeAction)}.`);
});
```

## off('availableDeviceChange')<sup>12+</sup>

off(type: 'availableDeviceChange', callback?: Callback<DeviceChangeAction\>): void

Unsubscribes from the event indicating that the connection status of an available audio device is changed.

**System capability**: SystemCapability.Multimedia.Audio.Device

**Parameters**

| Name  | Type                                               | Mandatory| Description                                      |
| -------- | --------------------------------------------------- | ---- | ------------------------------------------ |
| type     | string                                              | Yes   | Event type. This field has a fixed value of **'availableDeviceChange'**. |
| callback | Callback<[DeviceChangeAction](arkts-apis-audio-i.md#devicechangeaction)> | No   | Callback used to return the result. If a callback is passed, only the listener for events corresponding to this callback will be unregistered. The callback must be the same as that bound to [on('availableDeviceChange')](#onavailabledevicechange12). If no parameter is passed, all listeners for events of this event type will be unregistered.  |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**Example**

```ts
// Cancel all subscriptions to the event.
audioRoutingManager.off('availableDeviceChange');

// For the same event, if the callback parameter passed to the off API is the same as that passed to the on API, the off API cancels the subscription registered with the specified callback parameter.
let availableDeviceChangeCallback = (deviceChangeAction: audio.DeviceChangeAction) => {
  console.info(`Available device changed, deviceChangeAction: ${JSON.stringify(deviceChangeAction)}.`);
};

audioRoutingManager.on('availableDeviceChange', audio.DeviceUsage.MEDIA_OUTPUT_DEVICES, availableDeviceChangeCallback);

audioRoutingManager.off('availableDeviceChange', availableDeviceChangeCallback);
```

## setCommunicationDevice<sup>9+</sup>

setCommunicationDevice(deviceType: CommunicationDeviceType, active: boolean): Promise&lt;void&gt;

Sets a communication device to the active state. This API uses a promise to return the result.

This API will be deprecated in a later version due to function design is changed. You are not advised to use it.

You are advised to use the [AVCastPicker component](../../media/avsession/using-switch-call-devices.md) provided by AVSession to switch between call devices.

**System capability**: SystemCapability.Multimedia.Audio.Communication

**Parameters**

| Name    | Type                                                  | Mandatory| Description              |
| ---------- | ----------------------------------------------------- | ---- | ------------------ |
| deviceType | [CommunicationDeviceType](arkts-apis-audio-e.md#communicationdevicetype9)  | Yes  | Active audio device type.|
| active     | boolean                                               | Yes  | Active state to set. **true** to set the device to the active state, **false** otherwise.    |

**Return value**

| Type               | Description                           |
| ------------------- | ------------------------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioRoutingManager.setCommunicationDevice(audio.CommunicationDeviceType.SPEAKER, true).then(() => {
  console.info('Succeeded in setting the active status of the communication device.');
}).catch((err: BusinessError) => {
  console.error(`Failed to set the active status of the communication device. Code: ${err.code}, message: ${err.message}`);
});
```

## isCommunicationDeviceActive<sup>9+</sup>

isCommunicationDeviceActive(deviceType: CommunicationDeviceType, callback: AsyncCallback&lt;boolean&gt;): void

Checks whether a communication device is active. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.Audio.Communication

**Parameters**

| Name    | Type                                                 | Mandatory| Description                    |
| ---------- | ---------------------------------------------------- | ---- | ------------------------ |
| deviceType | [CommunicationDeviceType](arkts-apis-audio-e.md#communicationdevicetype9) | Yes   | Communication device type. |
| callback   | AsyncCallback&lt;boolean&gt;                         | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is **true** if the device is active or **false** if not active; otherwise, **err** is an error object.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioRoutingManager.isCommunicationDeviceActive(audio.CommunicationDeviceType.SPEAKER, (err: BusinessError, value: boolean) => {
  if (err) {
    console.error(`Failed to check whether the communication device is active. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in checking whether the communication device is active, isActive: ${value}.`);
});
```

## isCommunicationDeviceActive<sup>9+</sup>

isCommunicationDeviceActive(deviceType: CommunicationDeviceType): Promise&lt;boolean&gt;

Checks whether a communication device is active. This API uses a promise to return the result.

**System capability**: SystemCapability.Multimedia.Audio.Communication

**Parameters**

| Name    | Type                                                 | Mandatory| Description              |
| ---------- | ---------------------------------------------------- | ---- | ------------------ |
| deviceType | [CommunicationDeviceType](arkts-apis-audio-e.md#communicationdevicetype9) | Yes  | Active audio device type.|

**Return value**

| Type                  | Description                            |
| ---------------------- | ------------------------------- |
| Promise&lt;boolean&gt; | Promise used to return the result, indicating whether the device is active. **true** if active, **false** otherwise.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

audioRoutingManager.isCommunicationDeviceActive(audio.CommunicationDeviceType.SPEAKER).then((value: boolean) => {
  console.info(`Succeeded in checking whether the communication device is active, isActive: ${value}.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to check whether the communication device is active. Code: ${err.code}, message: ${err.message}`);
});
```

## isCommunicationDeviceActiveSync<sup>10+</sup>

isCommunicationDeviceActiveSync(deviceType: CommunicationDeviceType): boolean

Checks whether a communication device is active. This API returns the result synchronously.

**System capability**: SystemCapability.Multimedia.Audio.Communication

**Parameters**

| Name    | Type                                                 | Mandatory| Description              |
| ---------- | ---------------------------------------------------- | ---- | ------------------ |
| deviceType | [CommunicationDeviceType](arkts-apis-audio-e.md#communicationdevicetype9) | Yes  | Active audio device type.|

**Return value**

| Type                  | Description                            |
| ---------------------- | ------------------------------- |
| boolean | Check result for whether the device is active. **true** if active, **false** otherwise.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let value: boolean = audioRoutingManager.isCommunicationDeviceActiveSync(audio.CommunicationDeviceType.SPEAKER);
  console.info(`Succeeded in checking whether the communication device is active, isActive: ${value}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to check whether the communication device is active. Code: ${error.code}, message: ${error.message}`);
}
```

## getPreferOutputDeviceForRendererInfo<sup>10+</sup>

getPreferOutputDeviceForRendererInfo(rendererInfo: AudioRendererInfo, callback: AsyncCallback&lt;AudioDeviceDescriptors&gt;): void

Obtains the output device with the highest priority based on the audio renderer information. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.Audio.Device

**Parameters**

| Name                      | Type                                                        | Mandatory| Description                     |
| --------------------------- | ------------------------------------------------------------ | ---- | ------------------------- |
| rendererInfo                | [AudioRendererInfo](arkts-apis-audio-i.md#audiorendererinfo8)                     | Yes  | Audio renderer information.            |
| callback                    | AsyncCallback&lt;[AudioDeviceDescriptors](arkts-apis-audio-t.md#audiodevicedescriptors)&gt;  | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the output device with the highest priority obtained; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Error Codes](errorcode-audio.md).

| ID| Error Message                                          |
| ------- |--------------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. Return by callback. |
| 6800301 | System error. Return by callback.                |

**Example**
```ts
import { BusinessError } from '@kit.BasicServicesKit';

let rendererInfo: audio.AudioRendererInfo = {
  usage: audio.StreamUsage.STREAM_USAGE_MUSIC, // Audio stream usage type: music. Set this parameter based on the service scenario.
  rendererFlags: 0 // AudioRenderer flag.
};

audioRoutingManager.getPreferOutputDeviceForRendererInfo(rendererInfo, (err: BusinessError, audioDeviceDescriptors: audio.AudioDeviceDescriptors) => {
  if (err) {
    console.error(`Failed to obtain the preferred output device for renderer info. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in obtaining the preferred output device for renderer info, audioDeviceDescriptors: ${JSON.stringify(audioDeviceDescriptors)}.`);
});
```

## getPreferOutputDeviceForRendererInfo<sup>10+</sup>
getPreferOutputDeviceForRendererInfo(rendererInfo: AudioRendererInfo): Promise&lt;AudioDeviceDescriptors&gt;

Obtains the output device with the highest priority based on the audio renderer information. This API uses a promise to return the result.

**System capability**: SystemCapability.Multimedia.Audio.Device

**Parameters**

| Name                | Type                                                        | Mandatory| Description                     |
| ----------------------| ------------------------------------------------------------ | ---- | ------------------------- |
| rendererInfo          | [AudioRendererInfo](arkts-apis-audio-i.md#audiorendererinfo8)                     | Yes  | Audio renderer information.           |

**Return value**

| Type                 | Description                        |
| --------------------- | --------------------------- |
| Promise&lt;[AudioDeviceDescriptors](arkts-apis-audio-t.md#audiodevicedescriptors)&gt;   | Promise used to return the information about the output device with the highest priority.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Error Codes](errorcode-audio.md).

| ID| Error Message                                         |
| ------- |-------------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. Return by promise. |
| 6800301 | System error. Return by promise.                |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let rendererInfo: audio.AudioRendererInfo = {
  usage: audio.StreamUsage.STREAM_USAGE_MUSIC, // Audio stream usage type: music. Set this parameter based on the service scenario.
  rendererFlags: 0 // AudioRenderer flag.
};

audioRoutingManager.getPreferOutputDeviceForRendererInfo(rendererInfo).then((audioDeviceDescriptors: audio.AudioDeviceDescriptors) => {
  console.info(`Succeeded in obtaining the preferred output device for renderer info, audioDeviceDescriptors: ${JSON.stringify(audioDeviceDescriptors)}.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to obtain the preferred output device for renderer info. Code: ${err.code}, message: ${err.message}`);
});
```

## getPreferredOutputDeviceForRendererInfoSync<sup>10+</sup>
getPreferredOutputDeviceForRendererInfoSync(rendererInfo: AudioRendererInfo): AudioDeviceDescriptors

Obtains the output device with the highest priority based on the audio renderer information. This API returns the result synchronously.

**System capability**: SystemCapability.Multimedia.Audio.Device

**Parameters**

| Name                | Type                                                        | Mandatory| Description                     |
| ----------------------| ------------------------------------------------------------ | ---- | ------------------------- |
| rendererInfo          | [AudioRendererInfo](arkts-apis-audio-i.md#audiorendererinfo8)                     | Yes  | Audio renderer information.           |

**Return value**

| Type                 | Description                        |
| --------------------- | --------------------------- |
| [AudioDeviceDescriptors](arkts-apis-audio-t.md#audiodevicedescriptors)   | Information about the output device with the highest priority.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Error Codes](errorcode-audio.md).

| ID| Error Message                    |
| ------- |--------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let rendererInfo: audio.AudioRendererInfo = {
  usage: audio.StreamUsage.STREAM_USAGE_MUSIC, // Audio stream usage type: music. Set this parameter based on the service scenario.
  rendererFlags: 0 // AudioRenderer flag.
};

try {
  let audioDeviceDescriptors = audioRoutingManager.getPreferredOutputDeviceForRendererInfoSync(rendererInfo);
  console.info(`Succeeded in obtaining the preferred output device for renderer info, audioDeviceDescriptors: ${JSON.stringify(audioDeviceDescriptors)}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to obtain the preferred output device for renderer info. Code: ${error.code}, message: ${error.message}`);
}
```

## on('preferOutputDeviceChangeForRendererInfo')<sup>10+</sup>

on(type: 'preferOutputDeviceChangeForRendererInfo', rendererInfo: AudioRendererInfo, callback: Callback<AudioDeviceDescriptors\>): void

Subscribes to the change event of the output device with the highest priority, which is triggered when the output device with the highest priority is changed. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.Audio.Device

**Parameters**

| Name  | Type                                                | Mandatory| Description                                                     |
| :------- | :--------------------------------------------------- | :--- |:--------------------------------------------------------|
| type     | string | Yes  | Event type. The event **'preferOutputDeviceChangeForRendererInfo'** is triggered when the output device with the highest priority is changed.|
| rendererInfo  | [AudioRendererInfo](arkts-apis-audio-i.md#audiorendererinfo8)        | Yes  | Audio renderer information.                                               |
| callback | Callback<[AudioDeviceDescriptors](arkts-apis-audio-t.md#audiodevicedescriptors)\> | Yes  | Callback used to return the information about the output device with the highest priority.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**Example**

```ts
let rendererInfo: audio.AudioRendererInfo = {
  usage: audio.StreamUsage.STREAM_USAGE_MUSIC, // Audio stream usage type: music. Set this parameter based on the service scenario.
  rendererFlags: 0 // AudioRenderer flag.
};

audioRoutingManager.on('preferOutputDeviceChangeForRendererInfo', rendererInfo, (audioDeviceDescriptors: audio.AudioDeviceDescriptors) => {
  console.info(`Preferred output device changed, audioDeviceDescriptors: ${JSON.stringify(audioDeviceDescriptors)}.`);
});
```

## off('preferOutputDeviceChangeForRendererInfo')<sup>10+</sup>

off(type: 'preferOutputDeviceChangeForRendererInfo', callback?: Callback<AudioDeviceDescriptors\>): void

Unsubscribes from the change event of the output device with the highest priority.

**System capability**: SystemCapability.Multimedia.Audio.Device

**Parameters**

| Name  | Type                                               | Mandatory| Description                                      |
| -------- | --------------------------------------------------- | ---- | ------------------------------------------ |
| type     | string | Yes   | Event type. This field has a fixed value of **'preferOutputDeviceChangeForRendererInfo'**. |
| callback | Callback<[AudioDeviceDescriptors](arkts-apis-audio-t.md#audiodevicedescriptors)> | No   | Callback used to return the result. If a callback is passed, only the listener for events corresponding to this callback will be unregistered. The callback must be the same as that bound to [on('preferOutputDeviceChangeForRendererInfo')](#onpreferoutputdevicechangeforrendererinfo10). If no parameter is passed, all listeners for events of this event type will be unregistered.  |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**Example**

```ts
// For the same event, if the callback parameter passed to the off API is the same as that passed to the on API, the off API cancels the subscription registered with the specified callback parameter.
// If multiple subscriptions are made to the same event, you can call audioRoutingManager.off('preferOutputDeviceChangeForRendererInfo'); to cancel all of them.
let preferOutputDeviceChangeForRendererInfoCallback = (audioDeviceDescriptors: audio.AudioDeviceDescriptors) => {
  console.info(`Preferred output device changed, audioDeviceDescriptors: ${JSON.stringify(audioDeviceDescriptors)}.`);
};
let rendererInfo: audio.AudioRendererInfo = {
  usage: audio.StreamUsage.STREAM_USAGE_MUSIC, // Audio stream usage type: music. Set this parameter based on the service scenario.
  rendererFlags: 0 // AudioRenderer flag.
};

audioRoutingManager.on('preferOutputDeviceChangeForRendererInfo', rendererInfo, preferOutputDeviceChangeForRendererInfoCallback);

audioRoutingManager.off('preferOutputDeviceChangeForRendererInfo', preferOutputDeviceChangeForRendererInfoCallback);
```

## getPreferredInputDeviceForCapturerInfo<sup>10+</sup>

getPreferredInputDeviceForCapturerInfo(capturerInfo: AudioCapturerInfo, callback: AsyncCallback&lt;AudioDeviceDescriptors&gt;): void

Obtains the input device with the highest priority based on the audio capturer information. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.Audio.Device

**Parameters**

| Name                      | Type                                                        | Mandatory| Description                     |
| --------------------------- | ------------------------------------------------------------ | ---- | ------------------------- |
| capturerInfo                | [AudioCapturerInfo](arkts-apis-audio-i.md#audiocapturerinfo8)                     | Yes  | Audio capturer information.            |
| callback                    | AsyncCallback&lt;[AudioDeviceDescriptors](arkts-apis-audio-t.md#audiodevicedescriptors)&gt;  | Yes  | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the input device with the highest priority obtained; otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. Return by callback.|
| 6800301 | System error. Return by callback. |

**Example**
```ts
import { BusinessError } from '@kit.BasicServicesKit';

let capturerInfo: audio.AudioCapturerInfo = {
  source: audio.SourceType.SOURCE_TYPE_MIC, // Audio source type: microphone. Set this parameter based on the service scenario.
  capturerFlags: 0 // AudioCapturer flag.
};

audioRoutingManager.getPreferredInputDeviceForCapturerInfo(capturerInfo, (err: BusinessError, audioDeviceDescriptors: audio.AudioDeviceDescriptors) => {
  if (err) {
    console.error(`Failed to obtain the preferred input device for capturer info. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(`Succeeded in obtaining the preferred input device for capturer info, audioDeviceDescriptors: ${JSON.stringify(audioDeviceDescriptors)}.`);
});
```

## getPreferredInputDeviceForCapturerInfo<sup>10+</sup>

getPreferredInputDeviceForCapturerInfo(capturerInfo: AudioCapturerInfo): Promise&lt;AudioDeviceDescriptors&gt;

Obtains the input device with the highest priority based on the audio capturer information. This API uses a promise to return the result.

**System capability**: SystemCapability.Multimedia.Audio.Device

**Parameters**

| Name                | Type                                                        | Mandatory| Description                     |
| ----------------------| ------------------------------------------------------------ | ---- | ------------------------- |
| capturerInfo          | [AudioCapturerInfo](arkts-apis-audio-i.md#audiocapturerinfo8)                     | Yes  | Audio capturer information.           |

**Return value**

| Type                 | Description                        |
| --------------------- | --------------------------- |
| Promise&lt;[AudioDeviceDescriptors](arkts-apis-audio-t.md#audiodevicedescriptors)&gt;   | Promise used to return the information about the input device with the highest priority.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. Return by promise. |
| 6800301 | System error. Return by promise. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let capturerInfo: audio.AudioCapturerInfo = {
  source: audio.SourceType.SOURCE_TYPE_MIC, // Audio source type: microphone. Set this parameter based on the service scenario.
  capturerFlags: 0 // AudioCapturer flag.
};

audioRoutingManager.getPreferredInputDeviceForCapturerInfo(capturerInfo).then((audioDeviceDescriptors: audio.AudioDeviceDescriptors) => {
  console.info(`Succeeded in obtaining the preferred input device for capturer info, audioDeviceDescriptors: ${JSON.stringify(audioDeviceDescriptors)}.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to obtain the preferred input device for capturer info. Code: ${err.code}, message: ${err.message}`);
});
```

## getPreferredInputDeviceForCapturerInfoSync<sup>10+</sup>

getPreferredInputDeviceForCapturerInfoSync(capturerInfo: AudioCapturerInfo): AudioDeviceDescriptors

Obtains the input device with the highest priority based on the audio capturer information. This API returns the result synchronously.

**System capability**: SystemCapability.Multimedia.Audio.Device

**Parameters**

| Name                | Type                                                        | Mandatory| Description                     |
| ----------------------| ------------------------------------------------------------ | ---- | ------------------------- |
| capturerInfo          | [AudioCapturerInfo](arkts-apis-audio-i.md#audiocapturerinfo8)                     | Yes  | Audio capturer information.           |

**Return value**

| Type                 | Description                        |
| --------------------- | --------------------------- |
| [AudioDeviceDescriptors](arkts-apis-audio-t.md#audiodevicedescriptors)   | Information about the input device with the highest priority.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let capturerInfo: audio.AudioCapturerInfo = {
  source: audio.SourceType.SOURCE_TYPE_MIC, // Audio source type: microphone. Set this parameter based on the service scenario.
  capturerFlags: 0 // AudioCapturer flag.
};

try {
  let audioDeviceDescriptors = audioRoutingManager.getPreferredInputDeviceForCapturerInfoSync(capturerInfo);
  console.info(`Succeeded in obtaining the preferred input device for capturer info, audioDeviceDescriptors: ${JSON.stringify(audioDeviceDescriptors)}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to obtain the preferred input device for capturer info. Code: ${error.code}, message: ${error.message}`);
}
```

## on('preferredInputDeviceChangeForCapturerInfo')<sup>10+</sup>

on(type: 'preferredInputDeviceChangeForCapturerInfo', capturerInfo: AudioCapturerInfo, callback: Callback<AudioDeviceDescriptors\>): void

Subscribes to the change event of the input device with the highest priority, which is triggered when the input device with the highest priority is changed. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.Multimedia.Audio.Device

**Parameters**

| Name  | Type                                                | Mandatory| Description                                      |
| :------- | :--------------------------------------------------- | :--- | :----------------------------------------- |
| type     | string | Yes  | Event type. The event **'preferredInputDeviceChangeForCapturerInfo'** is triggered when the input device with the highest priority is changed.|
| capturerInfo  | [AudioCapturerInfo](arkts-apis-audio-i.md#audiocapturerinfo8)        | Yes  | Audio capturer information.             |
| callback | Callback<[AudioDeviceDescriptors](arkts-apis-audio-t.md#audiodevicedescriptors)\> | Yes  | Callback used to return the information about the input device with the highest priority.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**Example**

```ts
let capturerInfo: audio.AudioCapturerInfo = {
  source: audio.SourceType.SOURCE_TYPE_MIC, // Audio source type: microphone. Set this parameter based on the service scenario.
  capturerFlags: 0 // AudioCapturer flag.
};

audioRoutingManager.on('preferredInputDeviceChangeForCapturerInfo', capturerInfo, (audioDeviceDescriptors: audio.AudioDeviceDescriptors) => {
  console.info(`Preferred input device changed, audioDeviceDescriptors: ${JSON.stringify(audioDeviceDescriptors)}.`);
});
```

## off('preferredInputDeviceChangeForCapturerInfo')<sup>10+</sup>

off(type: 'preferredInputDeviceChangeForCapturerInfo', callback?: Callback<AudioDeviceDescriptors\>): void

Unsubscribes from the highest-priority input audio device change event.

**System capability**: SystemCapability.Multimedia.Audio.Device

**Parameters**

| Name  | Type                                               | Mandatory| Description                                      |
| -------- | --------------------------------------------------- | ---- | ------------------------------------------ |
| type     | string | Yes   | Event type. This field has a fixed value of **'preferredInputDeviceChangeForCapturerInfo'**. |
| callback | Callback<[AudioDeviceDescriptors](arkts-apis-audio-t.md#audiodevicedescriptors)> | No   | Callback used to return the result. If a callback is passed, only the listener for events corresponding to this callback will be unregistered. The callback must be the same as that bound to [on('preferredInputDeviceChangeForCapturerInfo')](#onpreferredinputdevicechangeforcapturerinfo10). If no parameter is passed, all listeners for events of this event type will be unregistered.  |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | --------------------------------------------|
| 401 | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| 6800101 | Parameter verification failed. |

**Example**

```ts
// For the same event, if the callback parameter passed to the off API is the same as that passed to the on API, the off API cancels the subscription registered with the specified callback parameter.
// If multiple subscriptions are made to the same event, you can call audioRoutingManager.off('preferredInputDeviceChangeForCapturerInfo'); to cancel all of them.
let preferredInputDeviceChangeForCapturerInfoCallback = (audioDeviceDescriptors: audio.AudioDeviceDescriptors) => {
  console.info(`Preferred input device changed, audioDeviceDescriptors: ${JSON.stringify(audioDeviceDescriptors)}.`);
};
let capturerInfo: audio.AudioCapturerInfo = {
  source: audio.SourceType.SOURCE_TYPE_MIC, // Audio source type: microphone. Set this parameter based on the service scenario.
  capturerFlags: 0 // AudioCapturer flag.
};

audioRoutingManager.on('preferredInputDeviceChangeForCapturerInfo', capturerInfo, preferredInputDeviceChangeForCapturerInfoCallback);

audioRoutingManager.off('preferredInputDeviceChangeForCapturerInfo', preferredInputDeviceChangeForCapturerInfoCallback);
```

## declareDeviceTypesCompatibility

declareDeviceTypesCompatibility(deviceTypes: DeviceTypeArray): void

Declares the device types that the app needs to be compatible with.

> **NOTE**
>
> For device types added in API version 20 or later, when an app calls an API (for example, [getAvailableDevices](arkts-apis-audio-AudioSessionManager.md#getavailabledevices21)) to obtain the device type, the returned device type is anonymous by default. To obtain the specific device type, call this method to declare the device type compatibility first.

**Since**: 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Device

**Parameters**

| Name | Type | Mandatory | Description |
| --------------------------- | ------------------------------------------------------------ | ---- | ------------------------- |
| deviceTypes | [DeviceTypeArray](arkts-apis-audio-t.md#devicetypearray) | Yes | [DeviceType](arkts-apis-audio-e.md#devicetype) array. |

**Error codes**

For details about the error codes, see [Audio Error Codes](errorcode-audio.md).

| ID | Error Message |
| ------- | --------------------------------------------|
| 6800101 | Parameter verification failed, the param deviceTypes contains value that is invalid enum or is not device type introduced in API 20 onwards. |

**Example**

```ts
let deviceTypes = [
  audio.DeviceType.NEARLINK
];

audioRoutingManager.declareDeviceTypesCompatibility(deviceTypes);
```