# AudioRoutingManager

```TypeScript
interface AudioRoutingManager
```

This interface implements audio routing management.

Before calling any API in AudioRoutingManager, you must use [getRoutingManager](arkts-audio-audio-audiomanager-i.md#getroutingmanager) to obtain an AudioRoutingManager instance.

> **NOTE:** 
> 
> - The initial APIs of this interface are supported since API version 9.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Audio.Device

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## declareDeviceTypesCompatibility

```TypeScript
declareDeviceTypesCompatibility(deviceTypes: DeviceTypeArray): void
```

Declares the original device types that the application has adapted to. By default, the system returns anonymous device types. This method allows applications to declare which specific device types they have explicitly adapted to. Once declared, the system will return the original device types to the application instead of the anonymous ones. Note: This method only supports device types introduced from API 20 onwards (such as hearing aids and nearlink devices). If this interface is not called for these new device types, the application will only be able to obtain anonymous device types. Legacy device types prior to API 20 do not need this declaration.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Device

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceTypes | [DeviceTypeArray](arkts-audio-audio-devicetypearray-t.md) | Yes | Array of original device types the application has adapted to. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed, the param deviceTypes contains value that is invalid enum or is not device type introduced in API 20 onwards. |

## getAvailableDevices

```TypeScript
getAvailableDevices(deviceUsage: DeviceUsage): AudioDeviceDescriptors
```

Obtains the available audio devices. This API returns the result synchronously.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Audio.Device

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceUsage | [DeviceUsage](arkts-audio-audio-deviceusage-e.md) | Yes | Audio device type (classified by usage). |

**Return value:**

| Type | Description |
| --- | --- |
| [AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md) | Device list. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let data: audio.AudioDeviceDescriptors = audioRoutingManager.getAvailableDevices(audio.DeviceUsage.MEDIA_OUTPUT_DEVICES);
  console.info('Succeeded in doing getAvailableDevices.');
} catch (err) {
  let error = err as BusinessError;
   console.error(`Failed to getAvailableDevices. Code: ${error.code}, message: ${error.message}`);
}
```

## getDevices

```TypeScript
getDevices(deviceFlag: DeviceFlag, callback: AsyncCallback<AudioDeviceDescriptors>): void
```

Obtains the audio devices with a specific flag. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Audio.Device

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceFlag | [DeviceFlag](arkts-audio-audio-deviceflag-e.md) | Yes | Audio device flag. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the audio devices obtained; otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioRoutingManager.getDevices(audio.DeviceFlag.OUTPUT_DEVICES_FLAG, (err: BusinessError, audioDeviceDescriptors: audio.AudioDeviceDescriptors) => {
  if (err) {
    console.error(`Failed to get devices. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info(`Succeeded in getting devices, AudioDeviceDescriptors: ${JSON.stringify(audioDeviceDescriptors)}.`);
  }
});
```

<a id="getdevices-1"></a>

## getDevices

```TypeScript
getDevices(deviceFlag: DeviceFlag): Promise<AudioDeviceDescriptors>
```

Obtains the audio devices with a specific flag. This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Audio.Device

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceFlag | [DeviceFlag](arkts-audio-audio-deviceflag-e.md) | Yes | Audio device flag. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md)&gt; | Promise used to return the device list. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioRoutingManager.getDevices(audio.DeviceFlag.OUTPUT_DEVICES_FLAG).then((audioDeviceDescriptors: audio.AudioDeviceDescriptors) => {
  console.info(`Succeeded in getting devices, AudioDeviceDescriptors: ${JSON.stringify(audioDeviceDescriptors)}.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get devices. Code: ${err.code}, message: ${err.message}`);
});
```

## getDevicesSync

```TypeScript
getDevicesSync(deviceFlag: DeviceFlag): AudioDeviceDescriptors
```

Obtains the audio devices with a specific flag. This API returns the result synchronously.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Audio.Device

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceFlag | [DeviceFlag](arkts-audio-audio-deviceflag-e.md) | Yes | Audio device flag. |

**Return value:**

| Type | Description |
| --- | --- |
| [AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md) | Device list. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let audioDeviceDescriptors = audioRoutingManager.getDevicesSync(audio.DeviceFlag.OUTPUT_DEVICES_FLAG);
  console.info(`Succeeded in getting devices, AudioDeviceDescriptors: ${JSON.stringify(audioDeviceDescriptors)}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get devices. Code: ${error.code}, message: ${error.message}`);
}
```

## getPreferOutputDeviceForRendererInfo

```TypeScript
getPreferOutputDeviceForRendererInfo(rendererInfo: AudioRendererInfo, callback: AsyncCallback<AudioDeviceDescriptors>): void
```

Obtains the output device with the highest priority based on the audio renderer information. This API uses an asynchronous callback to return the result.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Audio.Device

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rendererInfo | [AudioRendererInfo](arkts-audio-audio-audiorendererinfo-i.md) | Yes | Audio renderer information. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the output device with the highest priority obtained; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. Return by callback. |
| [6800301](../errorcode-audio.md#6800301-system-error) | System error. Return by callback. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let rendererInfo: audio.AudioRendererInfo = {
  usage: audio.StreamUsage.STREAM_USAGE_MUSIC, // Audio stream usage type: music. Set this parameter based on the service scenario.
  rendererFlags: 0 // AudioRenderer flag.
};

audioRoutingManager.getPreferOutputDeviceForRendererInfo(rendererInfo, (err: BusinessError, audioDeviceDescriptors: audio.AudioDeviceDescriptors) => {
  if (err) {
    console.error(`Failed to get prefer output device for renderer info. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info(`Succeeded in getting prefer output device for renderer info, AudioDeviceDescriptors: ${JSON.stringify(audioDeviceDescriptors)}.`);
  }
});
```

<a id="getpreferoutputdeviceforrendererinfo-1"></a>

## getPreferOutputDeviceForRendererInfo

```TypeScript
getPreferOutputDeviceForRendererInfo(rendererInfo: AudioRendererInfo): Promise<AudioDeviceDescriptors>
```

Obtains the output device with the highest priority based on the audio renderer information. This API uses a promise to return the result.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Audio.Device

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rendererInfo | [AudioRendererInfo](arkts-audio-audio-audiorendererinfo-i.md) | Yes | Audio renderer information. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md)&gt; | Promise used to return the information about the output device with the highest priority. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. Return by promise. |
| [6800301](../errorcode-audio.md#6800301-system-error) | System error. Return by promise. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let rendererInfo: audio.AudioRendererInfo = {
  usage: audio.StreamUsage.STREAM_USAGE_MUSIC, // Audio stream usage type: music. Set this parameter based on the service scenario.
  rendererFlags: 0 // AudioRenderer flag.
};

audioRoutingManager.getPreferOutputDeviceForRendererInfo(rendererInfo).then((audioDeviceDescriptors: audio.AudioDeviceDescriptors) => {
  console.info(`Succeeded in getting prefer output device for renderer info, AudioDeviceDescriptors: ${JSON.stringify(audioDeviceDescriptors)}.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get prefer output device for renderer info. Code: ${err.code}, message: ${err.message}`);
})
```

## getPreferredInputDeviceForCapturerInfo

```TypeScript
getPreferredInputDeviceForCapturerInfo(capturerInfo: AudioCapturerInfo, callback: AsyncCallback<AudioDeviceDescriptors>): void
```

Obtains the input device with the highest priority based on the audio capturer information. This API uses an asynchronous callback to return the result.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Audio.Device

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| capturerInfo | [AudioCapturerInfo](arkts-audio-audio-audiocapturerinfo-i.md) | Yes | Audio capturer information. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the input device with the highest priority obtained; otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. Return by callback. |
| [6800301](../errorcode-audio.md#6800301-system-error) | System error. Return by callback. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let capturerInfo: audio.AudioCapturerInfo = {
  source: audio.SourceType.SOURCE_TYPE_MIC, // Audio source type: microphone. Set this parameter based on the service scenario.
  capturerFlags: 0 // AudioCapturer flag.
};

audioRoutingManager.getPreferredInputDeviceForCapturerInfo(capturerInfo, (err: BusinessError, audioDeviceDescriptors: audio.AudioDeviceDescriptors) => {
  if (err) {
    console.error(`Failed to get preferred input device for capturer info. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info(`Succeeded in getting preferred input device for capturer info, AudioDeviceDescriptors: ${JSON.stringify(audioDeviceDescriptors)}.`);
  }
});
```

<a id="getpreferredinputdeviceforcapturerinfo-1"></a>

## getPreferredInputDeviceForCapturerInfo

```TypeScript
getPreferredInputDeviceForCapturerInfo(capturerInfo: AudioCapturerInfo): Promise<AudioDeviceDescriptors>
```

Obtains the input device with the highest priority based on the audio capturer information. This API uses a promise to return the result.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Audio.Device

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| capturerInfo | [AudioCapturerInfo](arkts-audio-audio-audiocapturerinfo-i.md) | Yes | Audio capturer information. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md)&gt; | Promise used to return the information about the input device with the highest priority. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. Return by promise. |
| [6800301](../errorcode-audio.md#6800301-system-error) | System error. Return by promise. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let capturerInfo: audio.AudioCapturerInfo = {
  source: audio.SourceType.SOURCE_TYPE_MIC, // Audio source type: microphone. Set this parameter based on the service scenario.
  capturerFlags: 0 // AudioCapturer flag.
};

audioRoutingManager.getPreferredInputDeviceForCapturerInfo(capturerInfo).then((audioDeviceDescriptors: audio.AudioDeviceDescriptors) => {
  console.info(`Succeeded in getting preferred input device for capturer info, AudioDeviceDescriptors: ${JSON.stringify(audioDeviceDescriptors)}.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get preferred input device for capturer info. Code: ${err.code}, message: ${err.message}`);
});
```

## getPreferredInputDeviceForCapturerInfoSync

```TypeScript
getPreferredInputDeviceForCapturerInfoSync(capturerInfo: AudioCapturerInfo): AudioDeviceDescriptors
```

Gets preferred input device for target audio capturer info.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Audio.Device

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| capturerInfo | [AudioCapturerInfo](arkts-audio-audio-audiocapturerinfo-i.md) | Yes | Audio capturer information. |

**Return value:**

| Type | Description |
| --- | --- |
| [AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md) | Information about the input device with the highest priority. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let capturerInfo: audio.AudioCapturerInfo = {
  source: audio.SourceType.SOURCE_TYPE_MIC, // Audio source type: microphone. Set this parameter based on the service scenario.
  capturerFlags: 0 // AudioCapturer flag.
};

try {
  let audioDeviceDescriptors = audioRoutingManager.getPreferredInputDeviceForCapturerInfoSync(capturerInfo);
  console.info(`Succeeded in getting preferred input device for capturer info, AudioDeviceDescriptors: ${JSON.stringify(audioDeviceDescriptors)}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get preferred input device for capturer info. Code: ${error.code}, message: ${error.message}`);
}
```

## getPreferredOutputDeviceForRendererInfoSync

```TypeScript
getPreferredOutputDeviceForRendererInfoSync(rendererInfo: AudioRendererInfo): AudioDeviceDescriptors
```

Obtains the output device with the highest priority based on the audio renderer information. This API returns the result synchronously.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Audio.Device

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rendererInfo | [AudioRendererInfo](arkts-audio-audio-audiorendererinfo-i.md) | Yes | Audio renderer information. |

**Return value:**

| Type | Description |
| --- | --- |
| [AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md) | Information about the output device with the highest priority. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let rendererInfo: audio.AudioRendererInfo = {
  usage: audio.StreamUsage.STREAM_USAGE_MUSIC, // Audio stream usage type: music. Set this parameter based on the service scenario.
  rendererFlags: 0 // AudioRenderer flag.
};

try {
  let audioDeviceDescriptors = audioRoutingManager.getPreferredOutputDeviceForRendererInfoSync(rendererInfo);
  console.info(`Succeeded in getting prefer output device for renderer info, AudioDeviceDescriptors: ${JSON.stringify(audioDeviceDescriptors)}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get prefer output device for renderer info. Code: ${error.code}, message: ${error.message}`);
}
```

## isCommunicationDeviceActive

```TypeScript
isCommunicationDeviceActive(deviceType: CommunicationDeviceType, callback: AsyncCallback<boolean>): void
```

Checks whether a communication device is active. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Audio.Communication

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceType | [CommunicationDeviceType](arkts-audio-audio-communicationdevicetype-e.md) | Yes | Active audio device type. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is **true** if the device is active or **false** if not active; otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioRoutingManager.isCommunicationDeviceActive(audio.CommunicationDeviceType.SPEAKER, (err: BusinessError, value: boolean) => {
  if (err) {
    console.error(`Failed to obtain the active status of the device. ${err}`);
    return;
  }
  console.info('Callback invoked to indicate that the active status of the device is obtained.');
});
```

<a id="iscommunicationdeviceactive-1"></a>

## isCommunicationDeviceActive

```TypeScript
isCommunicationDeviceActive(deviceType: CommunicationDeviceType): Promise<boolean>
```

Checks whether a communication device is active. This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Audio.Communication

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceType | [CommunicationDeviceType](arkts-audio-audio-communicationdevicetype-e.md) | Yes | Active audio device type. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result, indicating whether the device is active. **true** if active, **false** otherwise. |

**Examples**

```TypeScript
audioRoutingManager.isCommunicationDeviceActive(audio.CommunicationDeviceType.SPEAKER).then((value: boolean) => {
  console.info(`Promise returned to indicate that the active status of the device is obtained ${value}.`);
});
```

## isCommunicationDeviceActiveSync

```TypeScript
isCommunicationDeviceActiveSync(deviceType: CommunicationDeviceType): boolean
```

Checks whether a communication device is active. This API returns the result synchronously.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Audio.Communication

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceType | [CommunicationDeviceType](arkts-audio-audio-communicationdevicetype-e.md) | Yes | Active audio device type. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Check result for whether the device is active. **true** if active, **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let value: boolean = audioRoutingManager.isCommunicationDeviceActiveSync(audio.CommunicationDeviceType.SPEAKER);
  console.info(`Indicate that the active status of the device is obtained ${value}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to obtain the active status of the device ${error}.`);
}
```

## isMicBlockDetectionSupported

```TypeScript
isMicBlockDetectionSupported():Promise<boolean>
```

Checks whether the current device supports microphone blocking detection. This API uses a promise to return the result.

**Since:** 13

**System capability:** SystemCapability.Multimedia.Audio.Device

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Promise used to return the result, indicating the support for microphone blocking detection. **true** if supported, **false** otherwise. |

**Examples**

```TypeScript
audioRoutingManager.isMicBlockDetectionSupported().then((value: boolean) => {
  console.info(`Query whether microphone block detection is supported on current device result is ${value}.`);
});
```

## off('deviceChange')

```TypeScript
off(type: 'deviceChange', callback?: Callback<DeviceChangeAction>): void
```

Unsubscribes from the event indicating that the connection status of an audio device is changed. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Audio.Device

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'deviceChange' | Yes | Event type. The event **'deviceChange'** is triggered when the connection status of an audio device is changed. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[DeviceChangeAction](arkts-audio-audio-devicechangeaction-i.md)&gt; | No | Callback used to return the device change details. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
// Cancel all subscriptions to the event.
audioRoutingManager.off('deviceChange');

// For the same event, if the callback parameter passed to the off API is the same as that passed to the on API, the off API cancels the subscription registered with the specified callback parameter.
let deviceChangeCallback = (deviceChanged: audio.DeviceChangeAction) => {
  console.info('device change type : ' + deviceChanged.type);
  console.info('device descriptor size : ' + deviceChanged.deviceDescriptors.length);
  console.info('device change descriptor : ' + deviceChanged.deviceDescriptors[0].deviceRole);
  console.info('device change descriptor : ' + deviceChanged.deviceDescriptors[0].deviceType);
};

audioRoutingManager.on('deviceChange', audio.DeviceFlag.OUTPUT_DEVICES_FLAG, deviceChangeCallback);

audioRoutingManager.off('deviceChange', deviceChangeCallback);
```

## off('availableDeviceChange')

```TypeScript
off(type: 'availableDeviceChange', callback?: Callback<DeviceChangeAction>): void
```

Unsubscribes from the event indicating that the connection status of an available audio device is changed. This API uses an asynchronous callback to return the result.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Audio.Device

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'availableDeviceChange' | Yes | Event type. The event **'availableDeviceChange'** is triggered when the connection status of available audio devices is changed. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[DeviceChangeAction](arkts-audio-audio-devicechangeaction-i.md)&gt; | No | Callback used to return the available device change details. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
// Cancel all subscriptions to the event.
audioRoutingManager.off('availableDeviceChange');

// For the same event, if the callback parameter passed to the off API is the same as that passed to the on API, the off API cancels the subscription registered with the specified callback parameter.
let availableDeviceChangeCallback = (deviceChanged: audio.DeviceChangeAction) => {
  console.info('device change type : ' + deviceChanged.type);
  console.info('device descriptor size : ' + deviceChanged.deviceDescriptors.length);
  console.info('device change descriptor : ' + deviceChanged.deviceDescriptors[0].deviceRole);
  console.info('device change descriptor : ' + deviceChanged.deviceDescriptors[0].deviceType);
};

audioRoutingManager.on('availableDeviceChange', audio.DeviceUsage.MEDIA_OUTPUT_DEVICES, availableDeviceChangeCallback);

audioRoutingManager.off('availableDeviceChange', availableDeviceChangeCallback);
```

## off('preferOutputDeviceChangeForRendererInfo')

```TypeScript
off(type: 'preferOutputDeviceChangeForRendererInfo', callback?: Callback<AudioDeviceDescriptors>): void
```

Unsubscribes from the change event of the output device with the highest priority. This API uses an asynchronous callback to return the result.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Audio.Device

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'preferOutputDeviceChangeForRendererInfo' | Yes | Event type. The event **'preferOutputDeviceChangeForRendererInfo'** is triggered when the output device with the highest priority is changed. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md)&gt; | No | Callback used to return the information about the output device with the highest priority. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
// For the same event, if the callback parameter passed to the off API is the same as that passed to the on API, the off API cancels the subscription registered with the specified callback parameter.
// If multiple subscriptions are made to the same event, you can call audioRoutingManager.off('preferOutputDeviceChangeForRendererInfo'); to cancel all of them.
let preferOutputDeviceChangeForRendererInfoCallback = (audioDeviceDescriptors: audio.AudioDeviceDescriptors) => {
  console.info(`Succeeded in using on or off function, AudioDeviceDescriptors: ${JSON.stringify(audioDeviceDescriptors)}.`);
};
let rendererInfo: audio.AudioRendererInfo = {
  usage: audio.StreamUsage.STREAM_USAGE_MUSIC, // Audio stream usage type: music. Set this parameter based on the service scenario.
  rendererFlags: 0 // AudioRenderer flag.
};

audioRoutingManager.on('preferOutputDeviceChangeForRendererInfo', rendererInfo, preferOutputDeviceChangeForRendererInfoCallback);

audioRoutingManager.off('preferOutputDeviceChangeForRendererInfo', preferOutputDeviceChangeForRendererInfoCallback);
```

## off('preferredInputDeviceChangeForCapturerInfo')

```TypeScript
off(type: 'preferredInputDeviceChangeForCapturerInfo', callback?: Callback<AudioDeviceDescriptors>): void
```

Unsubscribes from the change event of the input device with the highest priority. This API uses an asynchronous callback to return the result.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Audio.Device

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'preferredInputDeviceChangeForCapturerInfo' | Yes | Event type. The event **'preferredInputDeviceChangeForCapturerInfo'** is triggered when the input device with the highest priority is changed. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md)&gt; | No | Callback used to return the information about the input device with the highest priority. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
// For the same event, if the callback parameter passed to the off API is the same as that passed to the on API, the off API cancels the subscription registered with the specified callback parameter.
// If multiple subscriptions are made to the same event, you can call audioRoutingManager.off('preferredInputDeviceChangeForCapturerInfo'); to cancel all of them.
let preferredInputDeviceChangeForCapturerInfoCallback = (audioDeviceDescriptors: audio.AudioDeviceDescriptors) => {
  console.info(`Succeeded in using on or off function, AudioDeviceDescriptors: ${JSON.stringify(audioDeviceDescriptors)}.`);
};
let capturerInfo: audio.AudioCapturerInfo = {
  source: audio.SourceType.SOURCE_TYPE_MIC, // Audio source type: microphone. Set this parameter based on the service scenario.
  capturerFlags: 0 // AudioCapturer flag.
};

audioRoutingManager.on('preferredInputDeviceChangeForCapturerInfo', capturerInfo, preferredInputDeviceChangeForCapturerInfoCallback);

audioRoutingManager.off('preferredInputDeviceChangeForCapturerInfo', preferredInputDeviceChangeForCapturerInfoCallback);
```

## off('micBlockStatusChanged')

```TypeScript
off(type: 'micBlockStatusChanged', callback?: Callback<DeviceBlockStatusInfo>): void
```

Unsubscribes from the microphone blocked status change event. This API uses an asynchronous callback to return the result.

**Since:** 13

**System capability:** SystemCapability.Multimedia.Audio.Device

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'micBlockStatusChanged' | Yes | Event type. The event **'micBlockStatusChanged'** is triggered when the microphone blocked status is changed. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[DeviceBlockStatusInfo](arkts-audio-audio-deviceblockstatusinfo-i.md)&gt; | No | Callback used to return the microphone blocked status and device information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
// Cancel all subscriptions to the event.
audioRoutingManager.off('micBlockStatusChanged');

// For the same event, if the callback parameter passed to the off API is the same as that passed to the on API, the off API cancels the subscription registered with the specified callback parameter.
let micBlockStatusCallback = (micBlockStatusChanged: audio.DeviceBlockStatusInfo) => {
  console.info(`block status : ${micBlockStatusChanged.blockStatus} `);
};

audioRoutingManager.on('micBlockStatusChanged', micBlockStatusCallback);

audioRoutingManager.off('micBlockStatusChanged', micBlockStatusCallback);
```

## on('deviceChange')

```TypeScript
on(type: 'deviceChange', deviceFlag: DeviceFlag, callback: Callback<DeviceChangeAction>): void
```

Subscribes to the event indicating that the connection status of an audio device is changed. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Audio.Device

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'deviceChange' | Yes | Event type. The event **'deviceChange'** is triggered when the connection status of an audio device is changed. |
| deviceFlag | [DeviceFlag](arkts-audio-audio-deviceflag-e.md) | Yes | Audio device flag. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[DeviceChangeAction](arkts-audio-audio-devicechangeaction-i.md)&gt; | Yes | Callback used to return the device change details. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
audioRoutingManager.on('deviceChange', audio.DeviceFlag.OUTPUT_DEVICES_FLAG, (deviceChanged: audio.DeviceChangeAction) => {
  console.info('device change type : ' + deviceChanged.type);
  console.info('device descriptor size : ' + deviceChanged.deviceDescriptors.length);
  console.info('device change descriptor : ' + deviceChanged.deviceDescriptors[0].deviceRole);
  console.info('device change descriptor : ' + deviceChanged.deviceDescriptors[0].deviceType);
});
```

## on('availableDeviceChange')

```TypeScript
on(type: 'availableDeviceChange', deviceUsage: DeviceUsage, callback: Callback<DeviceChangeAction>): void
```

Subscribes to the event indicating that the connection status of an available audio device is changed. This API uses an asynchronous callback to return the result.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Audio.Device

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'availableDeviceChange' | Yes | Event type. The event **'availableDeviceChange'** is triggered when the connection status of available audio devices is changed. |
| deviceUsage | [DeviceUsage](arkts-audio-audio-deviceusage-e.md) | Yes | Audio device type (classified by usage). |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[DeviceChangeAction](arkts-audio-audio-devicechangeaction-i.md)&gt; | Yes | Callback used to return the device change details. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
audioRoutingManager.on('availableDeviceChange', audio.DeviceUsage.MEDIA_OUTPUT_DEVICES, (deviceChanged: audio.DeviceChangeAction) => {
  console.info('device change type : ' + deviceChanged.type);
  console.info('device descriptor size : ' + deviceChanged.deviceDescriptors.length);
  console.info('device change descriptor : ' + deviceChanged.deviceDescriptors[0].deviceRole);
  console.info('device change descriptor : ' + deviceChanged.deviceDescriptors[0].deviceType);
});
```

## on('preferOutputDeviceChangeForRendererInfo')

```TypeScript
on(type: 'preferOutputDeviceChangeForRendererInfo', rendererInfo: AudioRendererInfo, callback: Callback<AudioDeviceDescriptors>): void
```

Subscribes to the change event of the output device with the highest priority, which is triggered when the output device with the highest priority is changed. This API uses an asynchronous callback to return the result.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Audio.Device

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'preferOutputDeviceChangeForRendererInfo' | Yes | Event type. The event **'preferOutputDeviceChangeForRendererInfo'** is triggered when the output device with the highest priority is changed. |
| rendererInfo | [AudioRendererInfo](arkts-audio-audio-audiorendererinfo-i.md) | Yes | Audio renderer information. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md)&gt; | Yes | Callback used to return the information about the output device with the highest priority. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
let rendererInfo: audio.AudioRendererInfo = {
  usage: audio.StreamUsage.STREAM_USAGE_MUSIC, // Audio stream usage type: music. Set this parameter based on the service scenario.
  rendererFlags: 0 // AudioRenderer flag.
};

audioRoutingManager.on('preferOutputDeviceChangeForRendererInfo', rendererInfo, (audioDeviceDescriptors: audio.AudioDeviceDescriptors) => {
  console.info(`Succeeded in using on function, AudioDeviceDescriptors: ${JSON.stringify(audioDeviceDescriptors)}.`);
});
```

## on('preferredInputDeviceChangeForCapturerInfo')

```TypeScript
on(type: 'preferredInputDeviceChangeForCapturerInfo', capturerInfo: AudioCapturerInfo, callback: Callback<AudioDeviceDescriptors>): void
```

Subscribes to the change event of the input device with the highest priority, which is triggered when the input device with the highest priority is changed. This API uses an asynchronous callback to return the result.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Audio.Device

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'preferredInputDeviceChangeForCapturerInfo' | Yes | Event type. The event **'preferredInputDeviceChangeForCapturerInfo'** is triggered when the input device with the highest priority is changed. |
| capturerInfo | [AudioCapturerInfo](arkts-audio-audio-audiocapturerinfo-i.md) | Yes | Audio capturer information. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md)&gt; | Yes | Callback used to return the information about the input device with the highest priority. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
let capturerInfo: audio.AudioCapturerInfo = {
  source: audio.SourceType.SOURCE_TYPE_MIC, // Audio source type: microphone. Set this parameter based on the service scenario.
  capturerFlags: 0 // AudioCapturer flag.
};

audioRoutingManager.on('preferredInputDeviceChangeForCapturerInfo', capturerInfo, (audioDeviceDescriptors: audio.AudioDeviceDescriptors) => {
  console.info(`Succeeded in using on function, AudioDeviceDescriptors: ${JSON.stringify(audioDeviceDescriptors)}.`);
});
```

## on('micBlockStatusChanged')

```TypeScript
on(type: 'micBlockStatusChanged', callback: Callback<DeviceBlockStatusInfo>): void
```

Subscribes to the microphone blocked status change event. This API uses an asynchronous callback to return the result.

Before using this API, check whether the current device supports microphone blocking detection. This event is triggered when the microphone blocked status changes during recording. Currently, this API takes effect only for the microphone on the local device.

**Since:** 13

**System capability:** SystemCapability.Multimedia.Audio.Device

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'micBlockStatusChanged' | Yes | Event type. The event **'micBlockStatusChanged'** is triggered when the microphone blocked status is changed. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[DeviceBlockStatusInfo](arkts-audio-audio-deviceblockstatusinfo-i.md)&gt; | Yes | Callback used to return the microphone blocked status and device information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
// Before the subscription, check whether the current device supports detection.
audioRoutingManager.isMicBlockDetectionSupported().then((value: boolean) => {
  console.info(`Query whether microphone block detection is supported on current device result is ${value}.`);
  if (value) {
    audioRoutingManager.on('micBlockStatusChanged', (micBlockStatusChanged: audio.DeviceBlockStatusInfo) => {
      console.info(`block status : ${micBlockStatusChanged.blockStatus} `);
    });
  }
});
```

## setCommunicationDevice

```TypeScript
setCommunicationDevice(deviceType: CommunicationDeviceType, active: boolean, callback: AsyncCallback<void>): void
```

Sets a communication device to the active state. This API uses an asynchronous callback to return the result.

This API will be deprecated in a later version due to function design is changed. You are not advised to use it.

You are advised to use the [AVCastPicker component](../../../media/avsession/using-switch-call-devices.md) provided by AVSession to switch between call devices.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Audio.Communication

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceType | [CommunicationDeviceType](arkts-audio-audio-communicationdevicetype-e.md) | Yes | Audio device flag. |
| active | boolean | Yes | Active state to set. **true** to set the device to the active state, **false** otherwise. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioRoutingManager.setCommunicationDevice(audio.CommunicationDeviceType.SPEAKER, true, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to set the active status of the device. ${err}`);
    return;
  }
  console.info('Callback invoked to indicate that the device is set to the active status.');
});
```

<a id="setcommunicationdevice-1"></a>

## setCommunicationDevice

```TypeScript
setCommunicationDevice(deviceType: CommunicationDeviceType, active: boolean): Promise<void>
```

Sets a communication device to the active state. This API uses a promise to return the result.

This API will be deprecated in a later version due to function design is changed. You are not advised to use it.

You are advised to use the [AVCastPicker component](../../../media/avsession/using-switch-call-devices.md) provided by AVSession to switch between call devices.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Audio.Communication

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceType | [CommunicationDeviceType](arkts-audio-audio-communicationdevicetype-e.md) | Yes | Active audio device type. |
| active | boolean | Yes | Active state to set. **true** to set the device to the active state, **false** otherwise. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
audioRoutingManager.setCommunicationDevice(audio.CommunicationDeviceType.SPEAKER, true).then(() => {
  console.info('Promise returned to indicate that the device is set to the active status.');
});
```
