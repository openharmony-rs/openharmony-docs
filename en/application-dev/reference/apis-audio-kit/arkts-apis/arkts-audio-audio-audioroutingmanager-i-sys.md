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

## excludeOutputDevices

```TypeScript
excludeOutputDevices(usage: DeviceUsage, devices: AudioDeviceDescriptors): Promise<void>
```

Exclude output devices. After calling this function successfully, audio will not be played on the specified devices. Note that only the external ouput device can be excluded by this function. Local output devices is not accepted.

**Since:** 18

**Required permissions:** 
- API version 23 and later: N/A
- API versions 18 to 22: ohos.permission.MANAGE_AUDIO_CONFIG

**System capability:** SystemCapability.Multimedia.Audio.Device

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| usage | [DeviceUsage](arkts-audio-audio-deviceusage-e.md) | Yes | Device usage, only output device usages can be accepted. |
| devices | [AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md) | Yes | The devices to be excluded. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permisson denied.<br>**Applicable version:** 18 - 22 |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let usage: audio.DeviceUsage.MEDIA_OUTPUT_DEVICES;
let excludedDevices: audio.AudioDeviceDescriptors = [{
  deviceRole : audio.DeviceRole.OUTPUT_DEVICE,
  deviceType : audio.DeviceType.BLUETOOTH_A2DP,
  id : 3,
  name : "",
  address : "",
  sampleRates : [44100],
  channelCounts : [2],
  channelMasks : [0],
  networkId : audio.LOCAL_NETWORK_ID,
  interruptGroupId : 1,
  volumeGroupId : 1,
  displayName : "",
}];

async function excludeOutputDevices(){
  audioRoutingManager.excludeOutputDevices(usage, excludedDevices, (err: BusinessError) => {
    if (err) {
      console.error(`Result ERROR: ${err}`);
    } else {
      console.info('Exclude Output Devices result callback: SUCCESS'); }
  });
}
```

## getActiveOutputDeviceDescriptors

```TypeScript
getActiveOutputDeviceDescriptors(): Promise<AudioDeviceDescriptors>
```

Gets the active output device descriptors for the current audio device. The activation policy is related to the audio device policy of the system.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Device

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md)&gt; | Promise used to get the output device descriptors. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not a system application. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
audioRoutingManager.getActiveOutputDeviceDescriptors().then((audioDeviceDescriptors: audio.AudioDeviceDescriptors) => {
  console.info(`Succeeded in getting active output device descriptors, AudioDeviceDescriptors: ${JSON.stringify(audioDeviceDescriptors)}.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get active output device descriptors. Code: ${err.code}, message: ${err.message}`);
});
```

## getExcludedDevices

```TypeScript
getExcludedDevices(usage: DeviceUsage): AudioDeviceDescriptors
```

Get excluded devices by filter.

**Since:** 18

**System capability:** SystemCapability.Multimedia.Audio.Device

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| usage | [DeviceUsage](arkts-audio-audio-deviceusage-e.md) | Yes | Device usage, only output device usages can be accepted. |

**Return value:**

| Type | Description |
| --- | --- |
| [AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md) | Exclueded devices. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit';

let usage: audio.DeviceUsage.MEDIA_OUTPUT_DEVICES;

async function getExcludedDevices(){
  let desc: audio.AudioDeviceDescriptors = audioRoutingManager.getExcludedDevices(usage);
  console.info(`device descriptor: ${desc}`);
}
```

## getPreferredInputDeviceByFilter

```TypeScript
getPreferredInputDeviceByFilter(filter: AudioCapturerFilter): AudioDeviceDescriptors
```

Get the preferred input device for the target audio capturer filter.

**Since:** 18

**System capability:** SystemCapability.Multimedia.Audio.Device

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| filter | [AudioCapturerFilter](arkts-audio-audio-audiocapturerfilter-i-sys.md) | Yes | Audio capturer filter. |

**Return value:**

| Type | Description |
| --- | --- |
| [AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md) | The preferred devices. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let inputAudioCapturerFilter: audio.AudioCapturerFilter = {
    uid : 20010041,
    capturerInfo : {
        source: audio.SourceType.SOURCE_TYPE_MIC,
        capturerFlags: 0
    }
};

async function getPreferredInputDeviceByFilter(){
    let audioManager = audio.getAudioManager();  // Create an AudioManager instance.
    let audioRoutingManager = audioManager.getRoutingManager();  // Call an API of AudioManager to create an AudioRoutingManager instance.
    let desc: audio.AudioDeviceDescriptors = audioRoutingManager.getPreferredInputDeviceByFilter(inputAudioCapturerFilter);
    console.info(`device descriptor: ${desc}`);
}
```

## getPreferredOutputDeviceByFilter

```TypeScript
getPreferredOutputDeviceByFilter(filter: AudioRendererFilter): AudioDeviceDescriptors
```

Get the preferred output devices by the target audio renderer filter.

**Since:** 18

**System capability:** SystemCapability.Multimedia.Audio.Device

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| filter | [AudioRendererFilter](arkts-audio-audio-audiorendererfilter-i-sys.md) | Yes | Audio renderer filter. |

**Return value:**

| Type | Description |
| --- | --- |
| [AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md) | The preferred devices. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let outputAudioRendererFilter: audio.AudioRendererFilter = {
  uid : 20010041,
  rendererInfo : {
    usage : audio.StreamUsage.STREAM_USAGE_MUSIC,
    rendererFlags : 0
  },
  rendererId : 0
};

async function selectOutputDeviceByFilter(){
    let audioManager = audio.getAudioManager();  // Create an AudioManager instance.
    let audioRoutingManager = audioManager.getRoutingManager();  // Call an API of AudioManager to create an AudioRoutingManager instance.
    let desc : audio.AudioDeviceDescriptors = audioRoutingManager.getPreferredOutputDeviceByFilter(outputAudioRendererFilter);
    console.info(`device descriptor: ${desc}`);
}
```

## off('preferredOutputDeviceChangeByFilter')

```TypeScript
off(type: 'preferredOutputDeviceChangeByFilter', callback?: Callback<AudioDeviceDescriptors>): void
```

UnSubscribes to prefer output device change events.

**Since:** 21

**System capability:** SystemCapability.Multimedia.Audio.Device

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'preferredOutputDeviceChangeByFilter' | Yes | Type of the event to listen for. Only the preferredOutputDeviceChangeByFilter event is supported. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md)&gt; | No | Callback used in subscribe. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [6800301](../errorcode-audio.md#6800301-system-error) | Audio client call audio service error, System error. |

**Examples**

```TypeScript
// Cancel all subscriptions to the event.
audioRoutingManager.off('preferredOutputDeviceChangeByFilter');

// For the same event, if the callback parameter passed to the off API is the same as that passed to the on API, the off API cancels the subscription registered with the specified callback parameter.
let preferredOutputDeviceChangeByFilterCallback = (audioDeviceDescriptors: audio.AudioDeviceDescriptors) => {
  console.info(`Succeeded in using on or off function, AudioDeviceDescriptors: ${JSON.stringify(audioDeviceDescriptors)}.`);
};
let outputAudioRendererFilter: audio.AudioRendererFilter = {
  uid : 20010041,
  rendererInfo : {
    usage : audio.StreamUsage.STREAM_USAGE_MUSIC,
    rendererFlags : 0
  },
  rendererId : 0
};

audioRoutingManager.on('preferredOutputDeviceChangeByFilter', outputAudioRendererFilter, preferredOutputDeviceChangeByFilterCallback);

audioRoutingManager.off('preferredOutputDeviceChangeByFilter', preferredOutputDeviceChangeByFilterCallback);
```

## offPreferredInputDeviceChangeByFilter

```TypeScript
offPreferredInputDeviceChangeByFilter(callback?: Callback<AudioDeviceDescriptors>): void
```

Unsubscribes to preferred input device change events.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Device

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md)&gt; | No | Callback used in subscribe. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [6800301](../errorcode-audio.md#6800301-system-error) | Audio client call audio service error, System error. |

**Examples**

```TypeScript
// Cancel all subscriptions to the event.
audioRoutingManager.offPreferredInputDeviceChangeByFilter();

// For the same event, if the callback parameter passed to the off API is the same as that passed to the on API, the off API cancels the subscription registered with the specified callback parameter.
let preferredInputDeviceChangeByFilterCallback = (audioDeviceDescriptors: audio.AudioDeviceDescriptors) => {
  console.info(`Succeeded in using onPreferredInputDeviceChangeByFilter or offPreferredInputDeviceChangeByFilter function, AudioDeviceDescriptors: ${JSON.stringify(audioDeviceDescriptors)}.`);
};
let inputAudioCapturerFilter: audio.AudioCapturerFilter = {
  uid : 20010041,
  capturerInfo : {
    source: audio.SourceType.SOURCE_TYPE_MIC,
    capturerFlags: 0
  }
};

audioRoutingManager.onPreferredInputDeviceChangeByFilter(inputAudioCapturerFilter, preferredInputDeviceChangeByFilterCallback);

audioRoutingManager.offPreferredInputDeviceChangeByFilter(preferredInputDeviceChangeByFilterCallback);
```

## on('preferredOutputDeviceChangeByFilter')

```TypeScript
on(type: 'preferredOutputDeviceChangeByFilter', filter: AudioRendererFilter, callback: Callback<AudioDeviceDescriptors>): void
```

Subscribes to prefer output device change events. When preferred device for target audio renderer filter changes, registered clients will receive the callback.

**Since:** 21

**System capability:** SystemCapability.Multimedia.Audio.Device

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'preferredOutputDeviceChangeByFilter' | Yes | Type of the event to listen for. Only the preferredOutputDeviceChangeByFilter event is supported. |
| filter | [AudioRendererFilter](arkts-audio-audio-audiorendererfilter-i-sys.md) | Yes | Filter for AudioRenderer. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md)&gt; | Yes | Callback used to obtain the changed prefer devices information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |
| [6800301](../errorcode-audio.md#6800301-system-error) | Audio client call audio service error, System error. |

**Examples**

```TypeScript
let outputAudioRendererFilter: audio.AudioRendererFilter = {
  uid : 20010041,
  rendererInfo : {
    usage : audio.StreamUsage.STREAM_USAGE_MUSIC,
    rendererFlags : 0
  },
  rendererId : 0
};
audioRoutingManager.on('preferredOutputDeviceChangeByFilter', outputAudioRendererFilter, (audioDeviceDescriptors: audio.AudioDeviceDescriptors) => {
  console.info(`Succeeded in using on function, AudioDeviceDescriptors: ${JSON.stringify(audioDeviceDescriptors)}.`);
});
```

## onPreferredInputDeviceChangeByFilter

```TypeScript
onPreferredInputDeviceChangeByFilter(filter: AudioCapturerFilter, callback: Callback<AudioDeviceDescriptors>): void
```

Subscribes to preferred input device change events. When the preferred device for target audio capturer filter changes, registered clients will receive a callback.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Device

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| filter | [AudioCapturerFilter](arkts-audio-audio-audiocapturerfilter-i-sys.md) | Yes | Filter for capturer. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md)&gt; | Yes | Callback to receive information about the changed preferred devices. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |
| [6800301](../errorcode-audio.md#6800301-system-error) | Audio client call audio service error, System error. |

**Examples**

```TypeScript
let inputAudioCapturerFilter: audio.AudioCapturerFilter = {
  uid : 20010041,
  capturerInfo : {
    source: audio.SourceType.SOURCE_TYPE_MIC,
    capturerFlags: 0
  }
};
audioRoutingManager.onPreferredInputDeviceChangeByFilter(inputAudioCapturerFilter, (audioDeviceDescriptors: audio.AudioDeviceDescriptors) => {
  console.info(`Succeeded in using onPreferredInputDeviceChangeByFilter function, AudioDeviceDescriptors: ${JSON.stringify(audioDeviceDescriptors)}.`);
});
```

## restoreOutputDeviceByFilter

```TypeScript
restoreOutputDeviceByFilter(filter: AudioRendererFilter): Promise<void>
```

Restores the output device for the specified audio renderer filter to the default strategy.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Device

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| filter | [AudioRendererFilter](arkts-audio-audio-audiorendererfilter-i-sys.md) | Yes | Filter of audio renderer to restore. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Caller is not a system application. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let outputAudioRendererFilter: audio.AudioRendererFilter = {
  uid : 20010041,
  rendererInfo : {
    usage : audio.StreamUsage.STREAM_USAGE_MUSIC,
    rendererFlags : 0
  },
  rendererId : 0
};

audioRoutingManager.restoreOutputDeviceByFilter(outputAudioRendererFilter).then(() => {
  console.info('Succeeded in restoring output device by filter.');
}).catch((err: BusinessError) => {
  console.error(`Failed to restore output device by filter. Code: ${err.code}, message: ${err.message}`);
});
```

## selectInputDevice

```TypeScript
selectInputDevice(inputAudioDevices: AudioDeviceDescriptors, callback: AsyncCallback<void>): void
```

Select the input device. This method uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Audio.Device

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| inputAudioDevices | [AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md) | Yes | Audio device description |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let inputAudioDeviceDescriptor: audio.AudioDeviceDescriptors = [{
  deviceRole : audio.DeviceRole.INPUT_DEVICE,
  deviceType : audio.DeviceType.MIC,
  id : 1,
  name : "",
  address : "",
  sampleRates : [44100],
  channelCounts : [2],
  channelMasks : [0],
  networkId : audio.LOCAL_NETWORK_ID,
  interruptGroupId : 1,
  volumeGroupId : 1,
  displayName : "",
}];

async function selectInputDevice(){
  audioRoutingManager.selectInputDevice(inputAudioDeviceDescriptor, (err: BusinessError) => {
    if (err) {
      console.error(`Result ERROR: ${err}`);
    } else {
      console.info('Select input devices result callback: SUCCESS');
    }
  });
}
```

<a id="selectinputdevice-1"></a>

## selectInputDevice

```TypeScript
selectInputDevice(inputAudioDevices: AudioDeviceDescriptors): Promise<void>
```

Select the input device. This method uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Audio.Device

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| inputAudioDevices | [AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md) | Yes | Audio device description |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let inputAudioDeviceDescriptor: audio.AudioDeviceDescriptors = [{
  deviceRole : audio.DeviceRole.INPUT_DEVICE,
  deviceType : audio.DeviceType.MIC,
  id : 1,
  name : "",
  address : "",
  sampleRates : [44100],
  channelCounts : [2],
  channelMasks : [0],
  networkId : audio.LOCAL_NETWORK_ID,
  interruptGroupId : 1,
  volumeGroupId : 1,
  displayName : "",
}];

async function getRoutingManager(){
  audioRoutingManager.selectInputDevice(inputAudioDeviceDescriptor).then(() => {
    console.info('Select input devices result promise: SUCCESS');
  }).catch((err: BusinessError) => {
    console.error(`Result ERROR: ${err}`);
  });
}
```

## selectInputDeviceByFilter

```TypeScript
selectInputDeviceByFilter(filter: AudioCapturerFilter, inputAudioDevices: AudioDeviceDescriptors): Promise<void>
```

Select the input device with desired AudioCapturer. This method uses a promise to return the result.

**Since:** 18

**System capability:** SystemCapability.Multimedia.Audio.Device

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| filter | [AudioCapturerFilter](arkts-audio-audio-audiocapturerfilter-i-sys.md) | Yes | Filter for AudioCapturer. |
| inputAudioDevices | [AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md) | Yes | Audio device descriptions |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let inputAudioCapturerFilter: audio.AudioCapturerFilter = {
    uid : 20010041,
    capturerInfo : {
        source: audio.SourceType.SOURCE_TYPE_MIC,
        capturerFlags: 0
    }
};

let inputAudioDeviceDescriptor: audio.AudioDeviceDescriptors = [{
    deviceRole : audio.DeviceRole.INPUT_DEVICE,
    deviceType : audio.DeviceType.MIC,
    id : 1,
    name : "",
    address : "",
    sampleRates : [44100],
    channelCounts : [2],
    channelMasks : [0],
    networkId : audio.LOCAL_NETWORK_ID,
    interruptGroupId : 1,
    volumeGroupId : 1,
    displayName : "",
}];

async function selectInputDeviceByFilter(){
    let audioManager = audio.getAudioManager();  // Create an AudioManager instance.
    let audioRoutingManager = audioManager.getRoutingManager();  // Call an API of AudioManager to create an AudioRoutingManager instance.
    audioRoutingManager.selectInputDeviceByFilter(inputAudioCapturerFilter, inputAudioDeviceDescriptor).then(() => {
        console.info('Select input devices by filter result promise: SUCCESS');
    }).catch((err: BusinessError) => {
        console.error(`Result ERROR: ${err}`);
    })
}
```

## selectOutputDevice

```TypeScript
selectOutputDevice(outputAudioDevices: AudioDeviceDescriptors, callback: AsyncCallback<void>): void
```

Select the output device. This method uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Audio.Device

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| outputAudioDevices | [AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md) | Yes | Audio device description |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let outputAudioDeviceDescriptor: audio.AudioDeviceDescriptors = [{
  deviceRole : audio.DeviceRole.OUTPUT_DEVICE,
  deviceType : audio.DeviceType.SPEAKER,
  id : 1,
  name : "",
  address : "",
  sampleRates : [44100],
  channelCounts : [2],
  channelMasks : [0],
  networkId : audio.LOCAL_NETWORK_ID,
  interruptGroupId : 1,
  volumeGroupId : 1,
  displayName : "",
}];

async function selectOutputDevice(){
  audioRoutingManager.selectOutputDevice(outputAudioDeviceDescriptor, (err: BusinessError) => {
    if (err) {
      console.error(`Result ERROR: ${err}`);
    } else {
      console.info('Select output devices result callback: SUCCESS'); }
  });
}
```

<a id="selectoutputdevice-1"></a>

## selectOutputDevice

```TypeScript
selectOutputDevice(outputAudioDevices: AudioDeviceDescriptors): Promise<void>
```

Select the output device. This method uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Audio.Device

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| outputAudioDevices | [AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md) | Yes | Audio device description |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let outputAudioDeviceDescriptor: audio.AudioDeviceDescriptors = [{
  deviceRole : audio.DeviceRole.OUTPUT_DEVICE,
  deviceType : audio.DeviceType.SPEAKER,
  id : 1,
  name : "",
  address : "",
  sampleRates : [44100],
  channelCounts : [2],
  channelMasks : [0],
  networkId : audio.LOCAL_NETWORK_ID,
  interruptGroupId : 1,
  volumeGroupId : 1,
  displayName : "",
}];

async function selectOutputDevice(){
  audioRoutingManager.selectOutputDevice(outputAudioDeviceDescriptor).then(() => {
    console.info('Select output devices result promise: SUCCESS');
  }).catch((err: BusinessError) => {
    console.error(`Result ERROR: ${err}`);
  });
}
```

## selectOutputDeviceByFilter

```TypeScript
selectOutputDeviceByFilter(filter: AudioRendererFilter, outputAudioDevices: AudioDeviceDescriptors, callback: AsyncCallback<void>): void
```

Select the output device with desired AudioRenderer. This method uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Audio.Device

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| filter | [AudioRendererFilter](arkts-audio-audio-audiorendererfilter-i-sys.md) | Yes | Filter for AudioRenderer. |
| outputAudioDevices | [AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md) | Yes | Audio device description. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let outputAudioRendererFilter: audio.AudioRendererFilter = {
  uid : 20010041,
  rendererInfo : {
    usage : audio.StreamUsage.STREAM_USAGE_MUSIC,
    rendererFlags : 0
  },
  rendererId : 0
};

let outputAudioDeviceDescriptor: audio.AudioDeviceDescriptors = [{
  deviceRole : audio.DeviceRole.OUTPUT_DEVICE,
  deviceType : audio.DeviceType.SPEAKER,
  id : 1,
  name : "",
  address : "",
  sampleRates : [44100],
  channelCounts : [2],
  channelMasks : [0],
  networkId : audio.LOCAL_NETWORK_ID,
  interruptGroupId : 1,
  volumeGroupId : 1,
  displayName : "",
}];

async function selectOutputDeviceByFilter(){
  audioRoutingManager.selectOutputDeviceByFilter(outputAudioRendererFilter, outputAudioDeviceDescriptor, (err: BusinessError) => {
    if (err) {
      console.error(`Result ERROR: ${err}`);
    } else {
      console.info('Select output devices by filter result callback: SUCCESS'); }
  });
}
```

<a id="selectoutputdevicebyfilter-1"></a>

## selectOutputDeviceByFilter

```TypeScript
selectOutputDeviceByFilter(filter: AudioRendererFilter, outputAudioDevices: AudioDeviceDescriptors): Promise<void>
```

Select the output device with desired AudioRenderer. This method uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Audio.Device

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| filter | [AudioRendererFilter](arkts-audio-audio-audiorendererfilter-i-sys.md) | Yes | Filter for AudioRenderer. |
| outputAudioDevices | [AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md) | Yes | Audio device description |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let outputAudioRendererFilter: audio.AudioRendererFilter = {
  uid : 20010041,
  rendererInfo : {
    usage : audio.StreamUsage.STREAM_USAGE_MUSIC,
    rendererFlags : 0
  },
  rendererId : 0
};

let outputAudioDeviceDescriptor: audio.AudioDeviceDescriptors = [{
  deviceRole : audio.DeviceRole.OUTPUT_DEVICE,
  deviceType : audio.DeviceType.SPEAKER,
  id : 1,
  name : "",
  address : "",
  sampleRates : [44100],
  channelCounts : [2],
  channelMasks : [0],
  networkId : audio.LOCAL_NETWORK_ID,
  interruptGroupId : 1,
  volumeGroupId : 1,
  displayName : "",
}];

async function selectOutputDeviceByFilter(){
  audioRoutingManager.selectOutputDeviceByFilter(outputAudioRendererFilter, outputAudioDeviceDescriptor).then(() => {
    console.info('Select output devices by filter result promise: SUCCESS');
  }).catch((err: BusinessError) => {
    console.error(`Result ERROR: ${err}`);
  })
}
```

<a id="selectoutputdevicebyfilter-2"></a>

## selectOutputDeviceByFilter

```TypeScript
selectOutputDeviceByFilter(filter: AudioRendererFilter, outputAudioDevices: AudioDeviceDescriptors, strategy: AudioDevcieSelectStrategy): Promise<void>
```

Select the output device with desired AudioRenderer. This method uses a promise to return the result.

**Since:** 21

**System capability:** SystemCapability.Multimedia.Audio.Device

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| filter | [AudioRendererFilter](arkts-audio-audio-audiorendererfilter-i-sys.md) | Yes | Filter for affected AudioRenderer. |
| outputAudioDevices | [AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md) | Yes | Audio device to select. |
| strategy | [AudioDevcieSelectStrategy](arkts-audio-audio-audiodevcieselectstrategy-e-sys.md) | Yes | Target audio device select strategy. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system App. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |
| [6800301](../errorcode-audio.md#6800301-system-error) | Audio client call audio service error, System error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let outputAudioRendererFilter: audio.AudioRendererFilter = {
  uid : 20010041,
  rendererInfo : {
    usage : audio.StreamUsage.STREAM_USAGE_MUSIC,
    rendererFlags : 0
  },
  rendererId : 0
};

let outputAudioDeviceDescriptor: audio.AudioDeviceDescriptors = [{
  deviceRole : audio.DeviceRole.OUTPUT_DEVICE,
  deviceType : audio.DeviceType.SPEAKER,
  id : 1,
  name : "",
  address : "",
  sampleRates : [44100],
  channelCounts : [2],
  channelMasks : [0],
  networkId : audio.LOCAL_NETWORK_ID,
  interruptGroupId : 1,
  volumeGroupId : 1,
  displayName : "",
}];

audioRoutingManager.selectOutputDeviceByFilter(outputAudioRendererFilter, outputAudioDeviceDescriptor, audio.AudioDevcieSelectStrategy.SELECT_STRATEGY_INDEPENDENT).then(() => {
  console.info('Succeeded in selecting output device by filter.');
}).catch((err: BusinessError) => {
  console.error(`Failed to select output device by filter. Code: ${err.code}, message: ${err.message}`);
});
```

## unexcludeOutputDevices

```TypeScript
unexcludeOutputDevices(usage: DeviceUsage, devices: AudioDeviceDescriptors): Promise<void>
```

Unexclude output devices. This function will unexclude target output devices belong to specific usage.

**Since:** 18

**Required permissions:** 
- API version 23 and later: N/A
- API versions 18 to 22: ohos.permission.MANAGE_AUDIO_CONFIG

**System capability:** SystemCapability.Multimedia.Audio.Device

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| usage | [DeviceUsage](arkts-audio-audio-deviceusage-e.md) | Yes | Device usage, only output device usages can be accepted. |
| devices | [AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md) | Yes | The devices to be unexcluded. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permisson denied.<br>**Applicable version:** 18 - 22 |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let usage: audio.DeviceUsage.MEDIA_OUTPUT_DEVICES;
let unexcludedDevices: audio.AudioDeviceDescriptors = [{
  deviceRole : audio.DeviceRole.OUTPUT_DEVICE,
  deviceType : audio.DeviceType.BLUETOOTH_A2DP,
  id : 3,
  name : "",
  address : "",
  sampleRates : [44100],
  channelCounts : [2],
  channelMasks : [0],
  networkId : audio.LOCAL_NETWORK_ID,
  interruptGroupId : 1,
  volumeGroupId : 1,
  displayName : "",
}];

async function unexcludeOutputDevices(){
  audioRoutingManager.unexcludeOutputDevices(usage, unexcludedDevices, (err: BusinessError) => {
    if (err) {
      console.error(`Result ERROR: ${err}`);
    } else {
      console.info('Unexclude Output Devices result callback: SUCCESS'); }
  });
}
```

<a id="unexcludeoutputdevices-1"></a>

## unexcludeOutputDevices

```TypeScript
unexcludeOutputDevices(usage: DeviceUsage): Promise<void>
```

Unexclude output devices. This function will unexclude all output devices belong to specific usage.

**Since:** 18

**Required permissions:** 
- API version 23 and later: N/A
- API versions 18 to 22: ohos.permission.MANAGE_AUDIO_CONFIG

**System capability:** SystemCapability.Multimedia.Audio.Device

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| usage | [DeviceUsage](arkts-audio-audio-deviceusage-e.md) | Yes | Device usage, only output device usages can be accepted. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permisson denied.<br>**Applicable version:** 18 - 22 |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let usage: audio.DeviceUsage.MEDIA_OUTPUT_DEVICES;

async function unexcludeOutputDevices(){
  audioRoutingManager.unexcludeOutputDevices(usage).then(() => {
    console.info('Unexclude Output Devices result promise: SUCCESS');
  }).catch((err: BusinessError) => {
    console.error(`Result ERROR: ${err}`);
  });
}
```
