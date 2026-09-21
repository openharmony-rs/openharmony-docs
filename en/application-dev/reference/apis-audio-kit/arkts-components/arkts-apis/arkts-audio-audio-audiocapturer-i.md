# AudioCapturer

```TypeScript
interface AudioCapturer
```

This interface provides APIs for audio capture.

Before calling any API in AudioCapturer, you must use [createAudioCapturer](arkts-audio-audio-createaudiocapturer-f.md) to create an AudioCapturer instance.

> **NOTE:** 
> 
> - The initial APIs of this interface are supported since API version 8.

**Since:** 8

**System capability:** SystemCapability.Multimedia.Audio.Capturer

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## getAudioStreamId

```TypeScript
getAudioStreamId(callback: AsyncCallback<number>): void
```

Obtains the stream ID of this audio capturer. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the stream ID obtained; otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioCapturer.getAudioStreamId((err: BusinessError, streamId: number) => {
  console.info(`audioCapturer GetStreamId: ${streamId}`);
});
```

<a id="getaudiostreamid-1"></a>

## getAudioStreamId

```TypeScript
getAudioStreamId(): Promise<number>
```

Obtains the stream ID of this audio capturer. This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the stream ID. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioCapturer.getAudioStreamId().then((streamId: number) => {
  console.info(`audioCapturer getAudioStreamId: ${streamId}`);
}).catch((err: BusinessError) => {
  console.error(`ERROR: ${err}`);
});
```

## getAudioStreamIdSync

```TypeScript
getAudioStreamIdSync(): number
```

Obtains the stream ID of this audio capturer. This API returns the result synchronously.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Return value:**

| Type | Description |
| --- | --- |
| number | Stream ID. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let streamId: number = audioCapturer.getAudioStreamIdSync();
  console.info(`audioCapturer getAudioStreamIdSync: ${streamId}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`ERROR: ${error}`);
}
```

## getAudioTime

```TypeScript
getAudioTime(callback: AsyncCallback<number>): void
```

Obtains the timestamp of the current recording position, measured in nanoseconds from the Unix epoch (January 1, 1970). This API uses an asynchronous callback to return the result.

**Since:** 8

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the number of nanoseconds obtained; otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioCapturer.getAudioTime((err: BusinessError, timestamp: number) => {
  console.info(`Succeeded in getting audio time. Timestamp: ${timestamp}`);
});
```

<a id="getaudiotime-1"></a>

## getAudioTime

```TypeScript
getAudioTime(): Promise<number>
```

Obtains the timestamp of the current recording position, measured in nanoseconds from the Unix epoch (January 1, 1970). This API uses a promise to return the result.

**Since:** 8

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return a timestamp representing the number of nanoseconds elapsed since the Unix epoch (January 1, 1970).<br>The timestamp unit is nanoseconds. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioCapturer.getAudioTime().then((timestamp: number) => {
  console.info(`Succeeded in getting audio time. Timestamp: ${timestamp}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get audio time. Code: ${err.code}, message: ${err.message}`);
});
```

## getAudioTimestampInfo

```TypeScript
getAudioTimestampInfo(): Promise<AudioTimestampInfo>
```

Obtains the timestamp and position information of an input audio stream.

This API obtains the actual recording position (specified by **framePos**) of the audio channel and the timestamp when recording to that position (specified by **timestamp**, in nanoseconds).

**Since:** 19

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AudioTimestampInfo](arkts-audio-audio-audiotimestampinfo-i.md)&gt; | Promise used to return the timestamp and position information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800103](../errorcode-audio.md#6800103-unsupported-state) | Operation not permit at current state. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioCapturer.getAudioTimestampInfo().then((audioTimestampInfo: audio.AudioTimestampInfo) => {
  console.info(`Current timestamp: ${audioTimestampInfo.timestamp}`);
}).catch((err: BusinessError) => {
  console.error(`ERROR: ${err}`);
});
```

## getAudioTimestampInfoSync

```TypeScript
getAudioTimestampInfoSync(): AudioTimestampInfo
```

Obtains the timestamp and position information of an input audio stream. This API returns the result synchronously.

**Since:** 19

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Return value:**

| Type | Description |
| --- | --- |
| [AudioTimestampInfo](arkts-audio-audio-audiotimestampinfo-i.md) | Information about the timestamp and position information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800103](../errorcode-audio.md#6800103-unsupported-state) | Operation not permit at current state. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let audioTimestampInfo: audio.AudioTimestampInfo = audioCapturer.getAudioTimestampInfoSync();
  console.info(`Current timestamp: ${audioTimestampInfo.timestamp}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`ERROR: ${error}`);
}
```

## getAudioTimeSync

```TypeScript
getAudioTimeSync(): number
```

Obtains the timestamp of the current recording position, measured in nanoseconds from the Unix epoch (January 1, 1970). This API returns the result synchronously.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Return value:**

| Type | Description |
| --- | --- |
| number | Timestamp. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let timestamp: number = audioCapturer.getAudioTimeSync();
  console.info(`Succeeded in getting audio time. Timestamp: ${timestamp}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get audio time. Code: ${error.code}, message: ${error.message}`);
}
```

## getBufferSize

```TypeScript
getBufferSize(callback: AsyncCallback<number>): void
```

Obtains a reasonable minimum buffer size in bytes for capturing. This API uses an asynchronous callback to return the result.

**Since:** 8

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the minimum buffer size obtained; otherwise, **err** is an error object.<br>The unit is bytes. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioCapturer.getBufferSize((err: BusinessError, bufferSize: number) => {
  if (err) {
    console.error(`Failed to get buffer size. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info(`Succeeded in getting buffer size, BufferSize: ${bufferSize}.`);
  }
});
```

<a id="getbuffersize-1"></a>

## getBufferSize

```TypeScript
getBufferSize(): Promise<number>
```

Obtains a reasonable minimum buffer size in bytes for capturing. This API uses a promise to return the result.

**Since:** 8

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the buffer size.<br>The unit is bytes. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioCapturer.getBufferSize().then((bufferSize: number) => {
  console.info(`Succeeded in getting buffer size, BufferSize: ${bufferSize}.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get buffer size. Code: ${err.code}, message: ${err.message}`);
});
```

## getBufferSizeSync

```TypeScript
getBufferSizeSync(): number
```

Obtains a reasonable minimum buffer size in bytes for capturing. This API returns the result synchronously.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Return value:**

| Type | Description |
| --- | --- |
| number | Buffer size, in bytes. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let bufferSize = audioCapturer.getBufferSizeSync();
  console.info(`Succeeded in getting buffer size, BufferSize: ${bufferSize}.`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get buffer size. Code: ${error.code}, message: ${error.message}`);
}
```

## getCapturerInfo

```TypeScript
getCapturerInfo(callback: AsyncCallback<AudioCapturerInfo>): void
```

Obtains the audio capturer information. This API uses an asynchronous callback to return the result.

**Since:** 8

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[AudioCapturerInfo](arkts-audio-audio-audiocapturerinfo-i.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the capturer information obtained; otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioCapturer.getCapturerInfo((err: BusinessError, capturerInfo: audio.AudioCapturerInfo) => {
  if (err) {
    console.error('Failed to get capture info');
  } else {
    console.info('Capturer getCapturerInfo:');
    console.info(`Capturer source: ${capturerInfo.source}`);
    console.info(`Capturer flags: ${capturerInfo.capturerFlags}`);
  }
});
```

<a id="getcapturerinfo-1"></a>

## getCapturerInfo

```TypeScript
getCapturerInfo(): Promise<AudioCapturerInfo>
```

Obtains the audio capturer information. This API uses a promise to return the result.

**Since:** 8

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AudioCapturerInfo](arkts-audio-audio-audiocapturerinfo-i.md)&gt; | Promise used to return the audio capturer information. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioCapturer.getCapturerInfo().then((audioParamsGet: audio.AudioCapturerInfo) => {
  if (audioParamsGet != undefined) {
    console.info('AudioFrameworkRecLog: Capturer CapturerInfo:');
    console.info(`AudioFrameworkRecLog: Capturer SourceType: ${audioParamsGet.source}`);
    console.info(`AudioFrameworkRecLog: Capturer capturerFlags: ${audioParamsGet.capturerFlags}`);
  } else {
    console.info(`AudioFrameworkRecLog: audioParamsGet is : ${audioParamsGet}`);
    console.info('AudioFrameworkRecLog: audioParams getCapturerInfo are incorrect');
  }
}).catch((err: BusinessError) => {
  console.error(`AudioFrameworkRecLog: CapturerInfo :ERROR: ${err}`);
})
```

## getCapturerInfoSync

```TypeScript
getCapturerInfoSync(): AudioCapturerInfo
```

Obtains the audio capturer information. This API returns the result synchronously.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Return value:**

| Type | Description |
| --- | --- |
| [AudioCapturerInfo](arkts-audio-audio-audiocapturerinfo-i.md) | Audio capturer information. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let audioParamsGet: audio.AudioCapturerInfo = audioCapturer.getCapturerInfoSync();
  console.info(`AudioFrameworkRecLog: Capturer SourceType: ${audioParamsGet.source}`);
  console.info(`AudioFrameworkRecLog: Capturer capturerFlags: ${audioParamsGet.capturerFlags}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`AudioFrameworkRecLog: CapturerInfo :ERROR: ${error}`);
}
```

## getCurrentAudioCapturerChangeInfo

```TypeScript
getCurrentAudioCapturerChangeInfo(): AudioCapturerChangeInfo
```

Obtains the configuration changes of the current audio capturer. This API returns the result synchronously.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Device

**Return value:**

| Type | Description |
| --- | --- |
| [AudioCapturerChangeInfo](arkts-audio-audio-audiocapturerchangeinfo-i.md) | Configuration changes of the audio capturer. |

**Examples**

```TypeScript
let info: audio.AudioCapturerChangeInfo = audioCapturer.getCurrentAudioCapturerChangeInfo();
console.info(`Info streamId: ${info.streamId}`);
console.info(`Info source: ${info.capturerInfo.source}`);
console.info(`Info capturerFlags: ${info.capturerInfo.capturerFlags}`);
console.info(`Info muted: ${info.muted}`);
console.info(`Info type: ${info.deviceDescriptors[0].deviceType}`);
console.info(`Info role: ${info.deviceDescriptors[0].deviceRole}`);
console.info(`Info name: ${info.deviceDescriptors[0].name}`);
console.info(`Info address: ${info.deviceDescriptors[0].address}`);
console.info(`Info samplerates: ${info.deviceDescriptors[0].sampleRates[0]}`);
console.info(`Info channelcounts: ${info.deviceDescriptors[0].channelCounts[0]}`);
console.info(`Info channelmask: ${info.deviceDescriptors[0].channelMasks[0]}`);
if (info.deviceDescriptors[0].encodingTypes) {
  console.info(`Device encodingTypes: ${info.deviceDescriptors[0].encodingTypes[0]}`);
}
```

## getCurrentInputDevices

```TypeScript
getCurrentInputDevices(): AudioDeviceDescriptors
```

Obtains the information of the current input devices. This API returns the result synchronously.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Device

**Return value:**

| Type | Description |
| --- | --- |
| [AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md) | An array of the audio device descriptors. |

**Examples**

```TypeScript
let deviceDescriptors: audio.AudioDeviceDescriptors = audioCapturer.getCurrentInputDevices();
console.info(`Device id: ${deviceDescriptors[0].id}`);
console.info(`Device type: ${deviceDescriptors[0].deviceType}`);
console.info(`Device role: ${deviceDescriptors[0].deviceRole}`);
console.info(`Device name: ${deviceDescriptors[0].name}`);
console.info(`Device address: ${deviceDescriptors[0].address}`);
console.info(`Device samplerates: ${deviceDescriptors[0].sampleRates[0]}`);
console.info(`Device channelcounts: ${deviceDescriptors[0].channelCounts[0]}`);
console.info(`Device channelmask: ${deviceDescriptors[0].channelMasks[0]}`);
if (deviceDescriptors[0].encodingTypes) {
  console.info(`Device encodingTypes: ${deviceDescriptors[0].encodingTypes[0]}`);
}
```

## getNoiseReductionMode

```TypeScript
getNoiseReductionMode(): NoiseReductionMode
```

Gets the noise reduction mode for current audio capturer. The mode will only consider the default and setted status, audio input device and stream concurrency will not be considered.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Return value:**

| Type | Description |
| --- | --- |
| [NoiseReductionMode](arkts-audio-audio-noisereductionmode-e.md) | The noise reduction mode for current audio capturer, the default value is [FIDELITY](arkts-audio-audio-noisereductionmode-e.md#fidelity). |

**Examples**

```TypeScript
let noiseReductionMode: audio.NoiseReductionMode = audioCapturer.getNoiseReductionMode();
console.info(`getNoiseReductionMode success: ${noiseReductionMode}`);
```

## getOverflowCount

```TypeScript
getOverflowCount(): Promise<number>
```

Obtains the number of overflow audio frames in the audio stream that is being captured. This API uses a promise to return the result.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the number of overflow audio frames. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioCapturer.getOverflowCount().then((value: number) => {
  console.info(`Get overflow count Success! ${value}`);
}).catch((err: BusinessError) => {
  console.error(`Get overflow count Fail: ${err}`);
});
```

## getOverflowCountSync

```TypeScript
getOverflowCountSync(): number
```

Obtains the number of overflow audio frames in the audio stream that is being captured. This API returns the result synchronously.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Return value:**

| Type | Description |
| --- | --- |
| number | Number of overflow audio frames. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let value: number = audioCapturer.getOverflowCountSync();
  console.info(`Get overflow count Success! ${value}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`Get overflow count Fail: ${error}`);
}
```

## getStreamInfo

```TypeScript
getStreamInfo(callback: AsyncCallback<AudioStreamInfo>): void
```

Obtains the stream information of this audio capturer. This API uses an asynchronous callback to return the result.

**Since:** 8

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[AudioStreamInfo](arkts-audio-audio-audiostreaminfo-i.md)&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the stream information obtained; otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioCapturer.getStreamInfo((err: BusinessError, streamInfo: audio.AudioStreamInfo) => {
  if (err) {
    console.error('Failed to get stream info');
  } else {
    console.info('Capturer GetStreamInfo:');
    console.info(`Capturer sampling rate: ${streamInfo.samplingRate}`);
    console.info(`Capturer channel: ${streamInfo.channels}`);
    console.info(`Capturer format: ${streamInfo.sampleFormat}`);
    console.info(`Capturer encoding type: ${streamInfo.encodingType}`);
  }
});
```

<a id="getstreaminfo-1"></a>

## getStreamInfo

```TypeScript
getStreamInfo(): Promise<AudioStreamInfo>
```

Obtains the stream information of this audio capturer. This API uses a promise to return the result.

**Since:** 8

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[AudioStreamInfo](arkts-audio-audio-audiostreaminfo-i.md)&gt; | Promise used to return the stream information. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioCapturer.getStreamInfo().then((audioParamsGet: audio.AudioStreamInfo) => {
  console.info('getStreamInfo:');
  console.info(`sampleFormat: ${audioParamsGet.sampleFormat}`);
  console.info(`samplingRate: ${audioParamsGet.samplingRate}`);
  console.info(`channels: ${audioParamsGet.channels}`);
  console.info(`encodingType: ${audioParamsGet.encodingType}`);
}).catch((err: BusinessError) => {
  console.error(`getStreamInfo :ERROR: ${err}`);
});
```

## getStreamInfoSync

```TypeScript
getStreamInfoSync(): AudioStreamInfo
```

Obtains the stream information of this audio capturer. This API returns the result synchronously.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Return value:**

| Type | Description |
| --- | --- |
| [AudioStreamInfo](arkts-audio-audio-audiostreaminfo-i.md) | Stream information. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let audioParamsGet: audio.AudioStreamInfo = audioCapturer.getStreamInfoSync();
  console.info(`sampleFormat: ${audioParamsGet.sampleFormat}`);
  console.info(`samplingRate: ${audioParamsGet.samplingRate}`);
  console.info(`channels: ${audioParamsGet.channels}`);
  console.info(`encodingType: ${audioParamsGet.encodingType}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`getStreamInfo :ERROR: ${error}`);
}
```

## getSupportedNoiseReductionModes

```TypeScript
getSupportedNoiseReductionModes(): Array<NoiseReductionMode>
```

Gets all the supported noise reduction modes for current device platform. Currently the noise reduction effect is only supported when using [SOURCE_TYPE_VOICE_MESSAGE](arkts-audio-audio-sourcetype-e.md#source_type_voice_message), other supported usage may be extened later. The supported modes will only consider the audio format and device platform, audio input device and stream concurrency will not be considered.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[NoiseReductionMode](arkts-audio-audio-noisereductionmode-e.md)&gt; | The supported noise reduction mode array, at least [FIDELITY](arkts-audio-audio-noisereductionmode-e.md#fidelity) is supported. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800301](../errorcode-audio.md#6800301-system-error) | Audio server process died. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let supportedModes: Array<audio.NoiseReductionMode> = audioCapturer.getSupportedNoiseReductionModes();
  console.info(`getSupportedNoiseReductionModes success: ${supportedModes}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`getSupportedNoiseReductionModes failed. Code: ${error.code}, message: ${error.message}`);
}
```

## off('markReach')

```TypeScript
off(type: 'markReach', callback?: Callback<number>): void
```

Unsubscribes from the mark reached event. This API uses an asynchronous callback to return the result.

**Since:** 8

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'markReach' | Yes | Event type. The event **'markReach'** is triggered when the number of frames captured reaches the value of the **frame** parameter. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | No | Callback used to return the value of the **frame** parameter.<br>**Since:** 18 |

**Examples**

```TypeScript
// Cancel all subscriptions to the event.
audioCapturer.off('markReach');

// For the same event, if the callback parameter passed to the off API is the same as that passed to the on API, the off API cancels the subscription registered with the specified callback parameter.
let markReachCallback = (position: number) => {
  if (position == 1000) {
    console.info('ON Triggered successfully');
  }
};

audioCapturer.on('markReach', 1000, markReachCallback);

audioCapturer.off('markReach', markReachCallback);
```

## off('periodReach')

```TypeScript
off(type: 'periodReach', callback?: Callback<number>): void
```

Unsubscribes from the period reached event. This API uses an asynchronous callback to return the result.

**Since:** 8

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'periodReach' | Yes | Event type. The event **'periodReach'** is triggered each time the number of frames captured reaches the value of the **frame** parameter. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | No | Callback used to return the value of the **frame** parameter.<br>**Since:** 18 |

**Examples**

```TypeScript
// Cancel all subscriptions to the event.
audioCapturer.off('periodReach');

// For the same event, if the callback parameter passed to the off API is the same as that passed to the on API, the off API cancels the subscription registered with the specified callback parameter.
let periodReachCallback = (position: number) => {
  if (position == 1000) {
    console.info('ON Triggered successfully');
  }
};

audioCapturer.on('periodReach', 1000, periodReachCallback);

audioCapturer.off('periodReach', periodReachCallback);
```

## off('stateChange')

```TypeScript
off(type: 'stateChange', callback?: Callback<AudioState>): void
```

Unsubscribes from the audio capturer state change event. This API uses an asynchronous callback to return the result.

**Since:** 18

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'stateChange' | Yes | Event type. The event **'stateChange'** is triggered when the listening for audio capturer state change event is canceled. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioState](arkts-audio-audio-audiostate-e.md)&gt; | No | Callback used to return the audio status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
// Cancel all subscriptions to the event.
audioCapturer.off('stateChange');

// For the same event, if the callback parameter passed to the off API is the same as that passed to the on API, the off API cancels the subscription registered with the specified callback parameter.
let stateChangeCallback = (state: audio.AudioState) => {
  if (state == 1) {
    console.info('audio capturer state is: STATE_PREPARED');
  }
  if (state == 2) {
    console.info('audio capturer state is: STATE_RUNNING');
  }
};

audioCapturer.on('stateChange', stateChangeCallback);

audioCapturer.off('stateChange', stateChangeCallback);
```

## off('audioInterrupt')

```TypeScript
off(type: 'audioInterrupt'): void
```

Unsubscribes from the audio interruption event.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Audio.Interrupt

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'audioInterrupt' | Yes | Event type. The event **'audioInterrupt'** is triggered when the audio focus is changed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
audioCapturer.off('audioInterrupt');
```

## off('inputDeviceChange')

```TypeScript
off(type: 'inputDeviceChange', callback?: Callback<AudioDeviceDescriptors>): void
```

Unsubscribes from the audio input device change event. This API uses an asynchronous callback to return the result.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Device

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'inputDeviceChange' | Yes | Event type. The event **'inputDeviceChange'** is triggered when an audio input device is changed. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md)&gt; | No | Callback used to return the information about the audio input device. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
// Cancel all subscriptions to the event.
audioCapturer.off('inputDeviceChange');

// For the same event, if the callback parameter passed to the off API is the same as that passed to the on API, the off API cancels the subscription registered with the specified callback parameter.
let inputDeviceChangeCallback = (deviceChangeInfo: audio.AudioDeviceDescriptors) => {
  console.info(`inputDevice id: ${deviceChangeInfo[0].id}`);
  console.info(`inputDevice deviceRole: ${deviceChangeInfo[0].deviceRole}`);
  console.info(`inputDevice deviceType: ${deviceChangeInfo[0].deviceType}`);
};

audioCapturer.on('inputDeviceChange', inputDeviceChangeCallback);

audioCapturer.off('inputDeviceChange', inputDeviceChangeCallback);
```

## off('audioCapturerChange')

```TypeScript
off(type: 'audioCapturerChange', callback?: Callback<AudioCapturerChangeInfo>): void
```

Unsubscribes from the audio capturer configuration change event. This API uses an asynchronous callback to return the result.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'audioCapturerChange' | Yes | Event type. The event **'audioCapturerChange'** is triggered when the audio capturer configuration is changed. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioCapturerChangeInfo](arkts-audio-audio-audiocapturerchangeinfo-i.md)&gt; | No | Callback used for unsubscription. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
// Cancel all subscriptions to the event.
audioCapturer.off('audioCapturerChange');

// For the same event, if the callback parameter passed to the off API is the same as that passed to the on API, the off API cancels the subscription registered with the specified callback parameter.
let audioCapturerChangeCallback = (capturerChangeInfo: audio.AudioCapturerChangeInfo) => {
  console.info(`Succeeded in using on or off function, AudioCapturerChangeInfo: ${capturerChangeInfo}.`);
};

audioCapturer.on('audioCapturerChange', audioCapturerChangeCallback);

audioCapturer.off('audioCapturerChange', audioCapturerChangeCallback);
```

## off('readData')

```TypeScript
off(type: 'readData', callback?: Callback<ArrayBuffer>): void
```

Unsubscribes from the audio data read event. This API uses an asynchronous callback to return the result.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'readData' | Yes | Event type. The event **'readData'** is triggered when audio stream data needs to be read. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;ArrayBuffer&gt; | No | Callback used to return the buffer from which the data is read. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
// Cancel all subscriptions to the event.
audioCapturer.off('readData');

// For the same event, if the callback parameter passed to the off API is the same as that passed to the on API, the off API cancels the subscription registered with the specified callback parameter.
let readDataCallback = (data: ArrayBuffer) => {
    console.info(`read data: ${data}`);
};

audioCapturer.on('readData', readDataCallback);

audioCapturer.off('readData', readDataCallback);
```

## on('markReach')

```TypeScript
on(type: 'markReach', frame: number, callback: Callback<number>): void
```

Subscribes to the mark reached event, which is triggered (only once) when the number of frames captured reaches the value of the **frame** parameter. This API uses an asynchronous callback to return the result.

For example, if **frame** is set to **100**, the callback is invoked when the number of captured frames reaches the 100th frame.

**Since:** 8

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'markReach' | Yes | Event type. The event **'markReach'** is triggered when the number of frames captured reaches the value of the **frame** parameter. |
| frame | number | Yes | Number of frames to trigger the event. The value must be greater than **0**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | Yes | Callback used to return the value of the **frame** parameter. |

**Examples**

```TypeScript
audioCapturer.on('markReach', 1000, (position: number) => {
  if (position == 1000) {
    console.info('ON Triggered successfully');
  }
});
```

## on('periodReach')

```TypeScript
on(type: 'periodReach', frame: number, callback: Callback<number>): void
```

Subscribes to the period reached event, which is triggered each time the number of frames captured reaches the value of the **frame** parameter. In other words, the information is reported periodically. This API uses an asynchronous callback to return the result.

For example, if **frame** is set to **10**, the callback is invoked each time 10 frames are captured, for example, when the number of frames captured reaches the 10th frame, 20th frame, and 30th frame.

**Since:** 8

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'periodReach' | Yes | Event type. The event **'periodReach'** is triggered each time the number of frames captured reaches the value of the **frame** parameter. |
| frame | number | Yes | Number of frames to trigger the event. The value must be greater than **0**. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;number&gt; | Yes | Callback used to return the value of the **frame** parameter. |

**Examples**

```TypeScript
audioCapturer.on('periodReach', 1000, (position: number) => {
  if (position == 1000) {
    console.info('ON Triggered successfully');
  }
});
```

## on('stateChange')

```TypeScript
on(type: 'stateChange', callback: Callback<AudioState>): void
```

Subscribes to the audio capturer state change event, which is triggered when the state of the audio capturer is changed. This API uses an asynchronous callback to return the result.

**Since:** 8

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'stateChange' | Yes | Event type. The event **'stateChange'** is triggered when the state of the audio capturer is changed. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioState](arkts-audio-audio-audiostate-e.md)&gt; | Yes | Callback used to return the audio status. |

**Examples**

```TypeScript
audioCapturer.on('stateChange', (state: audio.AudioState) => {
  if (state == 1) {
    console.info('audio capturer state is: STATE_PREPARED');
  }
  if (state == 2) {
    console.info('audio capturer state is: STATE_RUNNING');
  }
});
```

## on('audioInterrupt')

```TypeScript
on(type: 'audioInterrupt', callback: Callback<InterruptEvent>): void
```

Subscribes to the audio interruption event, which is triggered when the audio focus is changed. This API uses an asynchronous callback to return the result.

The AudioCapturer instance proactively gains the focus when the **start** event occurs and releases the focus when the **pause** or **stop** event occurs. Therefore, you do not need to request to gain or release the focus.

After this API is called, an [InterruptEvent](arkts-audio-audio-interruptevent-i.md) is received when the AudioCapturer instance fails to obtain the focus or an audio interruption event occurs (for example, the audio stream is interrupted by others). It is recommended that the application perform further processing based on the **InterruptEvent** information. For details, see [Introduction to Audio Focus](../../../media/audio/audio-playback-concurrency.md).

**Since:** 10

**System capability:** SystemCapability.Multimedia.Audio.Interrupt

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'audioInterrupt' | Yes | Event type. The event **'audioInterrupt'** is triggered when the audio focus is changed. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[InterruptEvent](arkts-audio-audio-interruptevent-i.md)&gt; | Yes | Callback used to return the event information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
import { audio } from '@kit.AudioKit';

let isCapturing: boolean = false; // An identifier specifying whether capturing is in progress.

audioCapturer.on('audioInterrupt', (interruptEvent: audio.InterruptEvent) => {
  // When an audio interruption event occurs, the AudioCapturer receives the interruptEvent callback and performs processing based on the content in the callback.
  // 1. (Optional) The AudioRenderer reads the value of interruptEvent.forceType to see whether the system has forcibly performed the operation.
  // Note: In the default focus strategy, INTERRUPT_HINT_RESUME maps to the force type INTERRUPT_SHARE, and others map to INTERRUPT_FORCE. Therefore, the value of forceType does not need to be checked.
  // 2. (Mandatory) The AudioRenderer then reads the value of interruptEvent.hintType and performs corresponding processing.
  if (interruptEvent.forceType == audio.InterruptForceType.INTERRUPT_FORCE) {
    // The audio focus event has been forcibly executed by the system. The application needs to update its status and displayed content.
    switch (interruptEvent.hintType) {
      case audio.InterruptHint.INTERRUPT_HINT_PAUSE:
        // The audio stream has been paused and temporarily loses the focus. It will receive the interruptEvent corresponding to resume when it is able to regain the focus.
        console.info('Force paused. Update capturing status and stop reading');
        isCapturing = false; // A simplified processing indicating several operations for switching the application to the paused state.
        break;
      case audio.InterruptHint.INTERRUPT_HINT_STOP:
        // The audio stream has been stopped and permanently loses the focus. The user must manually trigger the operation to resume capturing.
        console.info('Force stopped. Update capturing status and stop reading');
        isCapturing = false; // A simplified processing indicating several operations for switching the application to the paused state.
        break;
      default:
        console.info('Invalid interruptEvent');
        break;
    }
  } else if (interruptEvent.forceType == audio.InterruptForceType.INTERRUPT_SHARE) {
    // The audio focus event needs to be operated by the application, which can choose the processing mode. It is recommended that the application process the event according to the value of InterruptHint.
    switch (interruptEvent.hintType) {
      case audio.InterruptHint.INTERRUPT_HINT_RESUME:
        // It is recommended that the application continue capturing. (The audio stream has been forcibly paused and temporarily lost the focus. It can resume capturing now.)
        // The INTERRUPT_HINT_RESUME operation must be proactively executed by the application and cannot be forcibly executed by the system. Therefore, the INTERRUPT_HINT_RESUME event must map to INTERRUPT_SHARE.
        console.info('Resume force paused capturer or ignore');
        // To continue capturing, the application must perform the required operations.
        break;
      default:
        console.info('Invalid interruptEvent');
        break;
    }
  }
});
```

## on('inputDeviceChange')

```TypeScript
on(type: 'inputDeviceChange', callback: Callback<AudioDeviceDescriptors>): void
```

Subscribes to the audio input device change event, which is triggered when an audio input device is changed. This API uses an asynchronous callback to return the result.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Device

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'inputDeviceChange' | Yes | Event type. The event **'inputDeviceChange'** is triggered when an audio input device is changed. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md)&gt; | Yes | Callback used to return the updated information about the audio input device. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
audioCapturer.on('inputDeviceChange', (deviceChangeInfo: audio.AudioDeviceDescriptors) => {
  console.info(`inputDevice id: ${deviceChangeInfo[0].id}`);
  console.info(`inputDevice deviceRole: ${deviceChangeInfo[0].deviceRole}`);
  console.info(`inputDevice deviceType: ${deviceChangeInfo[0].deviceType}`);
});
```

## on('audioCapturerChange')

```TypeScript
on(type: 'audioCapturerChange', callback: Callback<AudioCapturerChangeInfo>): void
```

Subscribes to the audio capturer configuration change event, which is triggered when the audio recording stream status or device is changed. This API uses an asynchronous callback to return the result. The subscription is implemented asynchronously and the callback, which is triggered when the audio capturer configuration changes, may fail to reflect the actual condition.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'audioCapturerChange' | Yes | Event type. The event **'audioCapturerChange'** is triggered when the audio recording stream status or device is changed. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AudioCapturerChangeInfo](arkts-audio-audio-audiocapturerchangeinfo-i.md)&gt; | Yes | Callback used to return the current configuration and status information of the audio capturer. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
audioCapturer.on('audioCapturerChange', (capturerChangeInfo: audio.AudioCapturerChangeInfo) => {
  console.info(`Succeeded in using on function, AudioCapturerChangeInfo: ${capturerChangeInfo}.`);
});
```

## on('readData')

```TypeScript
on(type: 'readData', callback: Callback<ArrayBuffer>): void
```

Subscribes to the audio data read event, which is triggered when audio stream data needs to be read. This API uses an asynchronous callback to return the result.

The callback function is used only to read audio data. Do not call AudioCapturer APIs in it.

To eliminate power-on noise caused by the microphone hardware design, the first 100 ms of data after recording starts is typically muted.

**Since:** 11

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'readData' | Yes | Event type. The event **'readData'** is triggered when audio stream data needs to be read. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;ArrayBuffer&gt; | Yes | Callback used to return the buffer from which the data is read. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1.Mandatory parameters are left unspecified; 2.Incorrect parameter types. |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { fileIo as fs } from '@kit.CoreFileKit';
import { common } from '@kit.AbilityKit';

class Options {
  offset?: number;
  length?: number;
}

let bufferSize: number = 0;
// Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let path = context.cacheDir;
let filePath = path + '/StarWars10s-2C-48000-4SW.pcm';
let file: fs.File = fs.openSync(filePath, fs.OpenMode.READ_WRITE | fs.OpenMode.CREATE);
let readDataCallback = (buffer: ArrayBuffer) => {
  let options: Options = {
    offset: bufferSize,
    length: buffer.byteLength
  };
  fs.writeSync(file.fd, buffer, options);
  bufferSize += buffer.byteLength;
}

audioCapturer.on('readData', readDataCallback);

audioCapturer.start((err: BusinessError) => {
  if (err) {
    console.error('Capturer start failed.');
  } else {
    console.info('Capturer start success.');
  }
});
```

## read

```TypeScript
read(size: number, isBlockingRead: boolean, callback: AsyncCallback<ArrayBuffer>): void
```

Reads the buffer from the audio capturer. This method uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 11

**Substitutes:** readData

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| size | number | Yes | Number of bytes to read. |
| isBlockingRead | boolean | Yes | Whether to block the read operation. **true** to block, **false** otherwise. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;ArrayBuffer&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined** and **data** is the buffer read; otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioCapturer.getBufferSize().then((bufferSize: number) => {
  console.info('Succeeded in doing getBufferSize.');
  audioCapturer.read(bufferSize, true, (err: BusinessError, buffer: ArrayBuffer) => {
    if (err) {
      console.error(`Failed to read. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in doing read.');
  });
}).catch((err: BusinessError) => {
  console.error(`Failed to getBufferSize. Code: ${err.code}, message: ${err.message}`);
});
```

<a id="read-1"></a>

## read

```TypeScript
read(size: number, isBlockingRead: boolean): Promise<ArrayBuffer>
```

Reads the buffer. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 11

**Substitutes:** readData

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| size | number | Yes | Number of bytes to read. |
| isBlockingRead | boolean | Yes | Whether to block the read operation. **true** to block, **false** otherwise. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;ArrayBuffer&gt; | Promise used to return the data read from the buffer. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioCapturer.getBufferSize().then((bufferSize: number) => {
  console.info('Succeeded in doing getBufferSize.');
  audioCapturer.read(bufferSize, true).then((buffer: ArrayBuffer) => {
    console.info('Succeeded in doing read.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to read. Code: ${err.code}, message: ${err.message}`);
  });
}).catch((err: BusinessError) => {
  console.error(`Failed to getBufferSize. Code: ${err.code}, message: ${err.message}`);
});
```

## release

```TypeScript
release(callback: AsyncCallback<void>): void
```

Releases this audio capturer. This API uses an asynchronous callback to return the result.

**Since:** 8

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioCapturer.release((err: BusinessError) => {
  if (err) {
    console.error('capturer release failed');
  } else {
    console.info('capturer released.');
  }
});
```

<a id="release-1"></a>

## release

```TypeScript
release(): Promise<void>
```

Releases this audio capturer. This API uses a promise to return the result.

**Since:** 8

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioCapturer.release().then(() => {
  console.info('AudioFrameworkRecLog: ---------RELEASE RECORD---------');
  console.info('AudioFrameworkRecLog: Capturer release : SUCCESS');
  console.info(`AudioFrameworkRecLog: AudioCapturer : STATE : ${audioCapturer.state}`);
}).catch((err: BusinessError) => {
  console.error(`AudioFrameworkRecLog: Capturer stop: ERROR: ${err}`);
});
```

## requestPlaybackCaptureStart

```TypeScript
requestPlaybackCaptureStart(callback: Callback<PlaybackCaptureStartState>): void
```

Asynchronously request to start the playback capture stream. This function is non-blocking, which means system will continue to process user authorization and stream starting when receiving the start request. And the final result will be returned by callback.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.PlaybackCapture

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PlaybackCaptureStartState](arkts-audio-audio-playbackcapturestartstate-e.md)&gt; | Yes | Callback function used to receive the final result of start request. |

**Examples**

```TypeScript
audioCapturer.requestPlaybackCaptureStart((state: audio.PlaybackCaptureStartState) => {
  if (state === audio.PlaybackCaptureStartState.STATE_SUCCESS) {
    console.info('Succeeded in starting Playback capture.');
  } else {
    console.error(`Failed to start Playback capture. State: ${state}.`);
  }
});
```

## setIndependentAudioSessionStrategy

```TypeScript
setIndependentAudioSessionStrategy(strategy: AudioSessionStrategy, behavior: number): void
```

Sets the independent audio session strategy and behavior parameters.

> **NOTE:** 
> 
> If this API is called while an audio capturer is running, you must call the
> [start](#start) API again for
> the settings to take effect.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| strategy | [AudioSessionStrategy](arkts-audio-audio-audiosessionstrategy-i.md) | Yes | Audio session strategy. |
| behavior | number | Yes | Specifies the audio session behavior.<br>This can be a single flag or a bitwise OR combination of multiple flags.<br>For details about the supported audio session behaviors, see [AudioSessionBehaviorFlags](arkts-audio-audio-audiosessionbehaviorflags-e.md). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |
| [6800103](../errorcode-audio.md#6800103-unsupported-state) | Operation not permit at current state. |

**Examples**

```TypeScript
let strategy: audio.AudioSessionStrategy = {
  concurrencyMode: audio.AudioConcurrencyMode.CONCURRENCY_MIX_WITH_OTHERS
};
let behavior: number = audio.AudioSessionBehaviorFlags.MUTE_WHEN_INTERRUPTED;
audioCapturer.setIndependentAudioSessionStrategy(strategy, behavior);
```

## setMuteHint

```TypeScript
setMuteHint(mute: boolean): Promise<void>
```

Set mute hint for this capturer, this method is used as a hint for power optimization it does not mute the recording stream, only affects internal processing strategy.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mute | boolean | Yes | Use true if application recording stream muted by application if self. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800103](../errorcode-audio.md#6800103-unsupported-state) | Operation not permitted at current state, stream is not running. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioCapturer.setMuteHint(true).then(() => {
  console.info('setMuteHint Success!');
}).catch((err: BusinessError) => {
  console.error(`setMuteHint Fail: ${err}`);
});
```

## setNoiseReductionMode

```TypeScript
setNoiseReductionMode(noiseReductionMode: NoiseReductionMode): void
```

Sets noise reduction mode for current audio capturer. The supported mode should be obtained by [getSupportedNoiseReductionModes](#getsupportednoisereductionmodes). The actual effect may vary from different audio devices, and will be invalid when there are multiple recording streams running simultaneously. The mode can only be changed in created and stopped state.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| noiseReductionMode | [NoiseReductionMode](arkts-audio-audio-noisereductionmode-e.md) | Yes | The noise reduction mode to set. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800101](../errorcode-audio.md#6800101-invalid-parameter) | Parameter verification failed. |
| [6800103](../errorcode-audio.md#6800103-unsupported-state) | Illegal state, audio capturer is in running or released state. |
| [6800104](../errorcode-audio.md#6800104-unsupported-parameter-value) | The setted mode is not supported. |
| [6800301](../errorcode-audio.md#6800301-system-error) | Audio server process died. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let supportedModes: Array<audio.NoiseReductionMode> = audioCapturer.getSupportedNoiseReductionModes();
  if (supportedModes.includes(audio.NoiseReductionMode.PURE_VOCALS)) {
    audioCapturer.setNoiseReductionMode(audio.NoiseReductionMode.PURE_VOCALS);
  } else {
    audioCapturer.setNoiseReductionMode(audio.NoiseReductionMode.FIDELITY);
  }
  console.info(`setNoiseReductionMode success: ${audioCapturer.getNoiseReductionMode()}`);
} catch (err) {
  let error = err as BusinessError;
  console.error(`setNoiseReductionMode failed. Code: ${error.code}, message: ${error.message}`);
}
```

## setWillMuteWhenInterrupted

```TypeScript
setWillMuteWhenInterrupted(muteWhenInterrupted: boolean): Promise<void>
```

Sets whether to [mute the current audio recording stream when an audio interruption occurs](../../../media/audio/using-audiocapturer-for-recording.md#setting-the-mute-interruption-mode). This API uses a promise to return the result.

**Since:** 20

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| muteWhenInterrupted | boolean | Yes | Whether to mute the current audio recording stream during an audio interruption. **true** to mute, **false** otherwise. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [6800103](../errorcode-audio.md#6800103-unsupported-state) | Operation not permitted at current state. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioCapturer.setWillMuteWhenInterrupted(true).then(() => {
  console.info('setWillMuteWhenInterrupted Success!');
}).catch((err: BusinessError) => {
  console.error(`setWillMuteWhenInterrupted Fail: ${err}`);
});
```

## start

```TypeScript
start(callback: AsyncCallback<void>): void
```

Starts this audio capturer to start capturing audio data. This API uses an asynchronous callback to return the result.

**Since:** 8

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. If the operation fails, an error object with the following error code is returned:<br>Error code 6800301: indicates abnormal status, focus preemption failure, and abnormal system processing. For details, see system logs. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioCapturer.start((err: BusinessError) => {
  if (err) {
    console.error('Capturer start failed.');
  } else {
    console.info('Capturer start success.');
  }
});
```

<a id="start-1"></a>

## start

```TypeScript
start(): Promise<void>
```

Starts this audio capturer to start capturing audio data. This API uses a promise to return the result.

**Since:** 8

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise object, which indicates that the capturer is started successfully. If the operation fails, an error object with the following error code is returned:<br>Error code 6800301: indicates abnormal status, focus preemption failure, and abnormal system processing. For details, see system logs. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioCapturer.start().then(() => {
  console.info('Succeeded in doing start.');
  if (audioCapturer.state == audio.AudioState.STATE_RUNNING) {
    console.info('AudioFrameworkRecLog: AudioCapturer is in Running State');
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to start. Code: ${err.code}, message: ${err.message}`);
});
```

## stop

```TypeScript
stop(callback: AsyncCallback<void>): void
```

Stops this audio capturer, ceasing the input audio stream. This API uses an asynchronous callback to return the result.

**Since:** 8

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**; otherwise, **err** is an error object. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioCapturer.stop((err: BusinessError) => {
  if (err) {
    console.error('Capturer stop failed');
  } else {
    console.info('Capturer stopped.');
  }
});
```

<a id="stop-1"></a>

## stop

```TypeScript
stop(): Promise<void>
```

Stops this audio capturer, ceasing the input audio stream. This API uses a promise to return the result.

**Since:** 8

**System capability:** SystemCapability.Multimedia.Audio.Capturer

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

audioCapturer.stop().then(() => {
  console.info('Succeeded in doing stop.');
  if (audioCapturer.state == audio.AudioState.STATE_STOPPED){
    console.info('AudioFrameworkRecLog: State is Stopped:');
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to stop. Code: ${err.code}, message: ${err.message}`);
});
```

## state

```TypeScript
readonly state: AudioState
```

Audio capturer state.

**Type:** [AudioState](arkts-audio-audio-audiostate-e.md)

**Since:** 8

**System capability:** SystemCapability.Multimedia.Audio.Capturer
