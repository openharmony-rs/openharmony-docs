# Interface (AudioDeviceEnhanceManager)
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @zhanganxiang1-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

The audio device enhancement management feature is used for application-level audio device selection and stream-level audio device selection.

Before using the APIs of AudioDeviceEnhanceManager, you need to obtain an AudioDeviceEnhanceManager instance via [getDeviceEnhanceManager](arkts-apis-audio-AudioManager.md#getdeviceenhancemanager).

> **NOTE**
>
> Before using this feature, applications should call [isEnhancedRoutingSupported](#isenhancedroutingsupported) to confirm whether the system supports the audio device enhancement management feature.

**Since:** 26.0.0

## Modules to Import

```ts
import { audio } from '@kit.AudioKit';
```

## SoundCardType

Enumerates sound card types.

**Since:** 26.1.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.Audio.Core

| Name| Value| Description|
| :--- | :--- | :--- |
| ONBOARD | 0 | Onboard sound card. |
| USB | 1 | USB sound card. |

## SoundCardInfo

Describes the sound card information.

**Since:** 26.1.0

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.Audio.Core

| Name| Type| Read-Only| Optional| Description|
| :--- | :--- | :--- | :--- | :--- |
| name | string | Yes| No| Sound card name. The maximum length is 256.|
| vendor | string | Yes| No| Sound card vendor. The maximum length is 128.|
| model | string | Yes| No| Sound card model. The maximum length is 128.|
| busAddress | string | Yes| No| Sound card bus address. The maximum length is 256.|
| driver | string | Yes| No| Sound card driver. The maximum length is 128.|
| cardId | string | Yes| Yes| Sound card ID. The maximum length is 128. Default value: Default sound card ID of the onboard sound card.|
| cardType | [SoundCardType](#soundcardtype) | Yes| Yes| Sound card type. Default value: The default is the onboard sound card type.|


## isEnhancedRoutingSupported()

isEnhancedRoutingSupported(): boolean

Checks whether the system supports the enhanced routing capabilities provided by the current manager.

> **NOTE**
>
> - Enhanced routing capabilities include selecting input and output devices for applications or audio streams.
> - Before calling enhanced routing-related APIs, applications should call this API to confirm system support. Even for devices of the same type, support may vary across different models due to hardware limitations.
> - When the system does not support enhanced routing capabilities, calling the related APIs will not take effect, and the system will select the default input and output devices for the application or audio stream.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.Audio.DeviceEnhance

**Returns**

| Type| Description|
| ---------------------- | ------------------------------------------------------------ |
| boolean | Whether the system supports the enhanced routing capability. The value **true** indicates yes, and **false** indicates no.|

**Example**

```ts
import { audio } from '@kit.AudioKit';

let isSupported = audioDeviceEnhanceManager.isEnhancedRoutingSupported();
console.info(`Succeeded in querying whether enhanced routing is supported. Result: ${isSupported}.`);
```

## selectOutputDevice()

selectOutputDevice(outputDevice: AudioDeviceDescriptor): Promise&lt;void&gt;

Selects an output device for an application. This API uses a promise to return the result.

> **NOTE**
>
> - This setting applies to all playback streams created by the application, unless a specific stream has already been assigned a dedicated output device via [selectOutputDeviceForAudioRenderer](#selectoutputdeviceforaudiorenderer).
> - When implementing output device selection, the application can obtain the list of available output devices via [AudioRoutingManager.getAvailableDevices](arkts-apis-audio-AudioRoutingManager.md#getavailabledevices12) and retrieve the current preferred output device via [AudioRoutingManager.getPreferOutputDeviceForRendererInfo](arkts-apis-audio-AudioRoutingManager.md#getpreferoutputdeviceforrendererinfo10).
> - This selection becomes invalid when the application exits or the selected device goes offline. After the application restarts or the device comes back online, the setting needs to be reconfigured to take effect.
> - If the system does not support this feature, the default output device will be selected for the application.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.Audio.DeviceEnhance

**Parameters**

| Parameter| Type| Mandatory| Description|
| ----------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| outputDevice | [AudioDeviceDescriptor](arkts-apis-audio-i.md#audiodevicedescriptor) | Yes| Descriptor of the output device, which must be obtained from the device array returned by [AudioRoutingManager.getAvailableDevices](arkts-apis-audio-AudioRoutingManager.md#getavailabledevices12).|

**Returns**

| Type| Description|
| ------------------- | ------------------------------ |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | -------------------------------------------- |
| 6800101 | Parameter verification failed, for example, the selected device does not exist. |
| 6800301 | Audio service error occurs, such as the service died. |

**Example**

```ts
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let audioManager = audio.getAudioManager();
let audioSessionManager = audioManager.getSessionManager();
let outputDevice = audioSessionManager.getAvailableDevices(audio.DeviceUsage.MEDIA_OUTPUT_DEVICES)[0];
audioDeviceEnhanceManager.selectOutputDevice(outputDevice).then(() => {
  console.info('Succeeded in selecting output device.');
}).catch((err: BusinessError) => {
  console.error(`Failed to select output device. Code: ${err.code}, message: ${err.message}`);
});
```

## selectInputDevice()

selectInputDevice(inputDevice: AudioDeviceDescriptor): Promise&lt;void&gt;

Selects an input device for an application. This API uses a promise to return the result.

> **NOTE**
>
> - This setting applies to all recording streams created by the application, unless a specific stream has already been assigned a dedicated input device via [selectInputDeviceForAudioCapturer](#selectinputdeviceforaudiocapturer).
> - When implementing input device selection, the application can obtain the list of available input devices via [AudioRoutingManager.getAvailableDevices](arkts-apis-audio-AudioRoutingManager.md#getavailabledevices12) and retrieve the current preferred input device via [AudioRoutingManager.getPreferredInputDeviceForCapturerInfo](arkts-apis-audio-AudioRoutingManager.md#getpreferredinputdeviceforcapturerinfo10).
> - This selection becomes invalid when the application exits or the selected device goes offline. After the application restarts or the device comes back online, the setting needs to be reconfigured to take effect.
> - If the system does not support this feature, the default input device will be selected for the application.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.Audio.DeviceEnhance

**Parameters**

| Parameter| Type| Mandatory| Description|
| ----------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| inputDevice | [AudioDeviceDescriptor](arkts-apis-audio-i.md#audiodevicedescriptor) | Yes| Descriptor of the input device, which must be obtained from the device array returned by [AudioRoutingManager.getAvailableDevices](arkts-apis-audio-AudioRoutingManager.md#getavailabledevices12).|

**Returns**

| Type| Description|
| ------------------- | ------------------------------ |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | -------------------------------------------- |
| 6800101 | Parameter verification failed, for example, the selected device does not exist. |
| 6800301 | Audio service error occurs, such as the service died. |

**Example**

```ts
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let audioManager = audio.getAudioManager();
let audioSessionManager = audioManager.getSessionManager();
let inputDevice: audio.AudioDeviceDescriptor = audioSessionManager.getAvailableDevices(audio.DeviceUsage.MEDIA_INPUT_DEVICES)[0];
audioDeviceEnhanceManager.selectInputDevice(inputDevice).then(() => {
  console.info('Succeeded in selecting input device.');
}).catch((err: BusinessError) => {
  console.error(`Failed to select input device. Code: ${err.code}, message: ${err.message}`);
});
```

## selectOutputDeviceForAudioRenderer()

selectOutputDeviceForAudioRenderer(renderer: AudioRenderer, outputDevice: AudioDeviceDescriptor): Promise&lt;void&gt;

Sets the preferred output device for the specified audio playback stream. This API uses a promise to return the result.

> **NOTE**
>
> - The application must ensure that the specified AudioRenderer instance is valid.
> - This selection applies only to the specified audio stream. Other playback streams in the application will continue to use the application-level selected device or the system default output device.
> - This selection becomes invalid when the application exits or the selected device goes offline. After the application restarts or the device comes back online, the setting needs to be reconfigured to take effect.
> - If the system does not support this feature, the default output device will be used for the audio playback stream.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.Audio.DeviceEnhance

**Parameters**

| Parameter| Type| Mandatory| Description|
| ------------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| renderer | [AudioRenderer](arkts-apis-audio-AudioRenderer.md) | Yes| AudioRenderer instance.|
| outputDevice | [AudioDeviceDescriptor](arkts-apis-audio-i.md#audiodevicedescriptor) | Yes| Descriptor of the output device, which must be obtained from the device array returned by [AudioRoutingManager.getAvailableDevices](arkts-apis-audio-AudioRoutingManager.md#getavailabledevices12).|

**Returns**

| Type| Description|
| ------------------- | ------------------------------ |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | -------------------------------------------- |
| 6800101 | Parameter verification failed, for example, the selected device does not exist. |
| 6800301 | Audio service error occurs, such as the service died. |

**Example**

```ts
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let audioStreamInfo: audio.AudioStreamInfo = {
  samplingRate: audio.AudioSamplingRate.SAMPLE_RATE_48000, // Sampling rate.
  channels: audio.AudioChannel.CHANNEL_2, // Channel.
  sampleFormat: audio.AudioSampleFormat.SAMPLE_FORMAT_S16LE, // Sampling format.
  encodingType: audio.AudioEncodingType.ENCODING_TYPE_RAW // Encoding format.
};

let audioRendererInfo: audio.AudioRendererInfo = {
  usage: audio.StreamUsage.STREAM_USAGE_MUSIC, // Audio stream usage type: music. Set this parameter based on the service scenario. For details, see StreamUsage.
  rendererFlags: 0 // Audio renderer flag.
};

let audioRendererOptions: audio.AudioRendererOptions = {
  streamInfo: audioStreamInfo,
  rendererInfo: audioRendererInfo
};

let audioManager = audio.getAudioManager();
let audioSessionManager = audioManager.getSessionManager();
let outputDevice: audio.AudioDeviceDescriptor = audioSessionManager.getAvailableDevices(audio.DeviceUsage.MEDIA_OUTPUT_DEVICES)[0];

audio.createAudioRenderer(audioRendererOptions).then((data) => {
  console.info('AudioFrameworkRenderLog: AudioRenderer Created : SUCCESS');
  let audioRenderer = data;
  audioDeviceEnhanceManager.selectOutputDeviceForAudioRenderer(audioRenderer, outputDevice).then(() => {
    console.info('Succeeded in selecting output device for audio renderer.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to select output device for audio renderer. Code: ${err.code}, message: ${err.message}`);
  });
}).catch((err: BusinessError) => {
  console.error(`AudioFrameworkRenderLog: AudioRenderer Created : ERROR : ${err}`);
});
```

## getSoundCardInfoList()

getSoundCardInfoList(): Promise\<Array\<SoundCardInfo\>\>

Obtains the list of sound card information, including onboard sound cards and USB sound cards. This API uses a promise to return the result.

Application scenario: The application needs to obtain information about all audio adapters on the device, including onboard audio adapters and USB audio adapters, for asset management and monitoring.

**Since:** 26.1.0

**Model restriction**: This API can be used only in the stage model.

**Required permissions**: ohos.permission.GET_AUDIO_ADAPTER_INFO

**System capability**: SystemCapability.Multimedia.Audio.DeviceEnhance

**Return value**

| Type| Description|
| ------------------- | ------------------------------ |
| Promise\<Array\<[SoundCardInfo](#soundcardinfo)\>\> | Promise used to return the sound card information list.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message|
| ------- | -------------------------------------------- |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 801 | The current device model does not support this function. |

**Restriction**

- This API supports only PC devices. When a non-PC device invokes this API, error code 801 is returned.

**Example**

```ts
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let audioManager = audio.getAudioManager();
let deviceEnhanceManager = audioManager.getDeviceEnhanceManager();

deviceEnhanceManager.getSoundCardInfoList().then((soundCardInfoList: Array<audio.SoundCardInfo>) => {
  console.info(`Successfully obtained sound card info list: ${JSON.stringify(soundCardInfoList, null, 2)}`);
})
.catch((err: BusinessError) => {
  console.error(`Failed to get sound card info list. Code: ${err.code}, Message: ${err.message}`);
});
```

## selectInputDeviceForAudioCapturer()

selectInputDeviceForAudioCapturer(capturer: AudioCapturer, inputDevice: AudioDeviceDescriptor): Promise&lt;void&gt;

Sets the preferred input device for the specified audio recording stream. This API uses a promise to return the result.

> **NOTE**
>
> - The application must ensure that the specified AudioCapturer instance is valid.
> - This selection applies only to the specified audio stream. Other recording streams in the application will continue to use the application-level selected device or the system default input device.
> - This selection becomes invalid when the application exits or the selected device goes offline. After the application restarts or the device comes back online, the setting needs to be reconfigured to take effect.
> - If the system does not support this feature, the default input device will be used for the audio recording stream.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.Multimedia.Audio.DeviceEnhance

**Parameters**

| Parameter| Type| Mandatory| Description|
| ------------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| capturer | [AudioCapturer](arkts-apis-audio-AudioCapturer.md) | Yes| AudioCapturer instance.|
| inputDevice | [AudioDeviceDescriptor](arkts-apis-audio-i.md#audiodevicedescriptor) | Yes| Descriptor of the input device, which must be obtained from the device array returned by [AudioRoutingManager.getAvailableDevices](arkts-apis-audio-AudioRoutingManager.md#getavailabledevices12).|

**Returns**

| Type| Description|
| ------------------- | ------------------------------ |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Audio Error Codes](errorcode-audio.md).

| ID| Error Message|
| ------- | -------------------------------------------- |
| 6800101 | Parameter verification failed, for example, the selected device does not exist. |
| 6800301 | Audio service error occurs, such as the service died. |

**Example**

```ts
import { audio } from '@kit.AudioKit';
import { BusinessError } from '@kit.BasicServicesKit';

let audioStreamInfo: audio.AudioStreamInfo = {
  samplingRate: audio.AudioSamplingRate.SAMPLE_RATE_48000, // Sampling rate.
  channels: audio.AudioChannel.CHANNEL_2, // Channel.
  sampleFormat: audio.AudioSampleFormat.SAMPLE_FORMAT_S16LE, // Sampling format.
  encodingType: audio.AudioEncodingType.ENCODING_TYPE_RAW // Encoding format.
};

let audioCapturerInfo: audio.AudioCapturerInfo = {
  source: audio.SourceType.SOURCE_TYPE_MIC, // Audio source type: microphone. Set this parameter based on the service scenario. For details, see SourceType.
  capturerFlags: 0 // AudioCapturer flag.
};

let audioCapturerOptions: audio.AudioCapturerOptions = {
  streamInfo: audioStreamInfo,
  capturerInfo: audioCapturerInfo
};

let audioManager = audio.getAudioManager();
let audioSessionManager = audioManager.getSessionManager();
let inputDevice: audio.AudioDeviceDescriptor = audioSessionManager.getAvailableDevices(audio.DeviceUsage.MEDIA_INPUT_DEVICES)[0];

audio.createAudioCapturer(audioCapturerOptions).then((data) => {
  console.info('AudioCapturer Created : SUCCESS');
  let audioCapturer = data;
  audioDeviceEnhanceManager.selectInputDeviceForAudioCapturer(audioCapturer, inputDevice).then(() => {
    console.info('Succeeded in selecting input device for audio capturer.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to select input device for audio capturer. Code: ${err.code}, message: ${err.message}`);
  });
}).catch((err: BusinessError) => {
  console.error(`AudioCapturer Created : ERROR : ${err}`);
});
```
