# Interfaces (Other)
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @boxwall-->
<!--Designer: @magekkkk-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=1961de06e85063963f633ec54a8a4baaf5cb7dc8 translatedAt=2026-07-21T03:50:32.434Z pushedAt=2026-07-21T07:26:14.914Z -->

> **NOTE**
>
> The initial APIs of this module are supported since API version 7. Newly added APIs in subsequent versions are marked with a superscript to indicate their since version.

## AudioStreamInfo<sup>8+</sup>

Audio Stream Information.

**System capability:** SystemCapability.Multimedia.Audio.Core

| Name         | Type                                               | Read-only | Optional | Description               |
| ------------ | ------------------------------------------------- | ---- |---| ------------------ |
| samplingRate | [AudioSamplingRate](arkts-apis-audio-e.md#audiosamplingrate8) \| number| No | No | Audio sampling rate of the audio file, in Hz. Supports passing in [AudioSamplingRate](arkts-apis-audio-e.md#audiosamplingrate8).<br>Since API version 26.0.0:<br>- The samplingRate parameter supports the number type.<br>- Audio rendering extends support for sampling rate values from 8000 Hz to 384000 Hz in steps of 10 Hz. The supported sampling rate specifications may vary depending on the device.|
| channels     | [AudioChannel](arkts-apis-audio-e.md#audiochannel8)                    | No | No | Number of audio channels in the audio file. |
| sampleFormat | [AudioSampleFormat](arkts-apis-audio-e.md#audiosampleformat8)          | No | No | Audio sample format.     |
| encodingType | [AudioEncodingType](arkts-apis-audio-e.md#audioencodingtype8)          | No | No | Audio encoding format.     |
| channelLayout<sup>11+</sup> | [AudioChannelLayout](arkts-apis-audio-e.md#audiochannellayout11)  | No | Yes | Audio channel layout. Default value: 0x0. |

## AudioRendererInfo<sup>8+</sup>

Audio Renderer Information.

| Name          | Type                        | Read-only | Optional | Description            |
| ------------- | --------------------------- | ---- |---| --------------- |
| content<sup>(deprecated)</sup> | [ContentType](arkts-apis-audio-e.md#contenttypedeprecated) | No | Yes | Audio content type.<br/>**System capability:** SystemCapability.Multimedia.Audio.Core <br>This parameter was mandatory in API versions 8 and 9, and became optional since API version 10. Default value: CONTENT_TYPE_UNKNOWN.<br>Supported since API version 8 and deprecated since API version 10. You are advised to use usage instead. |
| usage         | [StreamUsage](arkts-apis-audio-e.md#streamusage) | No | No | Audio stream usage type.<br/>**System capability:** SystemCapability.Multimedia.Audio.Core <br/>**Atomic service API:** This API can be used in atomic services since API version 12.|
| rendererFlags | number                      | No | No | Playback stream behavior flag.<br>Set this to 0.<br/>**System capability:** SystemCapability.Multimedia.Audio.Core <br/>**Atomic service API:** This API can be used in atomic services since API version 12.|
| volumeMode<sup>19+</sup> | [AudioVolumeMode](arkts-apis-audio-e.md#audiovolumemode19) | No | Yes | Audio volume mode. Default value: SYSTEM_GLOBAL.<br/>**System capability:** SystemCapability.Multimedia.Audio.Volume|

## AudioRendererOptions<sup>8+</sup>

Audio renderer option information.

| Name         | Type                                     | Read-only | Optional | Description             |
| ------------ | ---------------------------------------- | ---- |---| ---------------- |
| streamInfo   | [AudioStreamInfo](#audiostreaminfo8)     | No | No | Audio stream information.<br/>**System capability:** SystemCapability.Multimedia.Audio.Renderer |
| rendererInfo | [AudioRendererInfo](#audiorendererinfo8) | No | No | Audio renderer information.<br/>**System capability:** SystemCapability.Multimedia.Audio.Renderer |
| privacyType<sup>10+</sup> | [AudioPrivacyType](arkts-apis-audio-e.md#audioprivacytype10) | No | Yes | Whether the audio stream can be recorded by other apps. Default value: 0.<br/>**System capability:** SystemCapability.Multimedia.Audio.PlaybackCapture |

## InterruptEvent<sup>9+</sup>

Interrupt event received by the app when an audio interruption occurs.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Multimedia.Audio.Renderer

| Name      | Type                                       | Read Only | Optional | Description                                 |
| --------- | ------------------------------------------ | --------- | -------- | ------------------------------------------- |
| eventType | [InterruptType](arkts-apis-audio-e.md#interrupttype)            | No  | No  | Audio interruption event type, which can be start or end.         |
| forceType | [InterruptForceType](arkts-apis-audio-e.md#interruptforcetype9) | No  | No  | Whether the operation is enforced by the system or performed by the app. |
| hintType  | [InterruptHint](arkts-apis-audio-e.md#interrupthint)            | No  | No  | Interruption hint, which provides information about the interruption event. |

## DeviceBlockStatusInfo<sup>13+</sup>

Describes the audio device block status and device information.

**System capability:** SystemCapability.Multimedia.Audio.Device

| Name              | Type                                              | Read-only | Optional | Description               |
| :---------------- | :------------------------------------------------ | :--- |---| :----------------- |
| blockStatus       | [DeviceBlockStatus](arkts-apis-audio-e.md#deviceblockstatus13)           | No | No | Audio device block status. |
| devices | [AudioDeviceDescriptors](arkts-apis-audio-t.md#audiodevicedescriptors) | No | No | Device information.         |

## AudioSessionStrategy<sup>12+</sup>

Audio session strategy.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Multimedia.Audio.Core

| Name          | Type                                              | Read-only | Optional | Description             |
| :------------ |:------------------------------------------------| :--- |---| :--------------- |
| concurrencyMode        | [AudioConcurrencyMode](arkts-apis-audio-e.md#audioconcurrencymode12) | No | No | Audio concurrency mode.       |

## AudioSessionDeactivatedEvent<sup>12+</sup>

Audio session deactivation event.

**System capability:** SystemCapability.Multimedia.Audio.Core

| Name          | Type                                                                | Read Only | Optional | Description             |
| :------------ |:------------------------------------------------------------------| :--- |---| :--------------- |
| reason        | [AudioSessionDeactivatedReason](arkts-apis-audio-e.md#audiosessiondeactivatedreason12) | No | No | Audio session deactivation reason.       |

## AudioSessionStateChangedEvent<sup>20+</sup>

Audio session state change event.

**System capability:** SystemCapability.Multimedia.Audio.Core

| Name          | Type                                              | Read-only | Optional | Description             |
| :------------ |:------------------------------------------------| :--- |---| :--------------- |
| stateChangeHint        | [AudioSessionStateChangeHint](arkts-apis-audio-e.md#audiosessionstatechangehint20) | No | No | Audio session state change hint. |

## AudioRendererChangeInfo<sup>9+</sup>

Describes the audio renderer change information.

**System capability:** SystemCapability.Multimedia.Audio.Renderer

| Name              | Type                                      | Read-Only | Optional | Description                          |
| -------------------| ----------------------------------------- | --------- | -------- | ------------------------------------ |
| streamId           | number                                    | Yes       | No       | Unique Audio Stream ID.              |
| rendererInfo       | [AudioRendererInfo](#audiorendererinfo8)  | Yes       | No       | Audio Renderer Information.          |
| deviceDescriptors  | [AudioDeviceDescriptors](arkts-apis-audio-t.md#audiodevicedescriptors)      | Yes       | No       | Audio device description.            |

## AudioCapturerChangeInfo<sup>9+</sup>

Describes audio capturer change information.

**System capability:** SystemCapability.Multimedia.Audio.Capturer

| Name              | Type                                      | Read-only | Optional | Description                          |
| -------------------| ----------------------------------------- | ---- | ---- | ---------------------------- |
| streamId           | number                                    | Yes   | No   | Unique audio stream ID.                |
| capturerInfo       | [AudioCapturerInfo](#audiocapturerinfo8)  | Yes   | No   | Audio capturer information.               |
| deviceDescriptors  | [AudioDeviceDescriptors](arkts-apis-audio-t.md#audiodevicedescriptors)      | Yes   | No   | Audio device information.|
| muted<sup>11+</sup>  | boolean    | Yes   | Yes | Whether the audio capturer is muted. The value true means muted, and false means not muted.|

## AudioDeviceDescriptor

Describes an audio device.

| Name                          | Type                       | Read Only | Optional | Description       |
| ----------------------------- | -------------------------- | ---- | ---- | ---------- |
| deviceRole                    | [DeviceRole](arkts-apis-audio-e.md#devicerole)  | Yes   | No   | Device role. <br> **System capability:** SystemCapability.Multimedia.Audio.Device <br/>**Atomic service API:** This API can be used in atomic services since API version 12.|
| deviceType                    | [DeviceType](arkts-apis-audio-e.md#devicetype)  | Yes   | No   | Device type. <br> **System capability:** SystemCapability.Multimedia.Audio.Device <br/>**Atomic service API:** This API can be used in atomic services since API version 12.|
| id<sup>9+</sup>               | number                     | Yes   | No   | Unique device ID.  <br> **System capability:** SystemCapability.Multimedia.Audio.Device <br/>**Atomic service API:** This API can be used in atomic services since API version 12.|
| name<sup>9+</sup>             | string                     | Yes   | No   | Device name.<br>For a Bluetooth device, the ohos.permission.USE_BLUETOOTH permission is required. <br> **System capability:** SystemCapability.Multimedia.Audio.Device <br/>**Atomic service API:** This API can be used in atomic services since API version 12.|
| address<sup>9+</sup>          | string                     | Yes   | No   | Device static MAC address.<br>For a Bluetooth device, the ohos.permission.USE_BLUETOOTH permission is required. <br> **System capability:** SystemCapability.Multimedia.Audio.Device <br/>**Atomic service API:** This API can be used in atomic services since API version 12.|
| sampleRates<sup>9+</sup>      | Array&lt;number&gt;        | Yes   | No   | Supported sampling rates. <br> **System capability:** SystemCapability.Multimedia.Audio.Device <br/>**Atomic service API:** This API can be used in atomic services since API version 12.|
| channelCounts<sup>9+</sup>    | Array&lt;number&gt;        | Yes   | No   | Supported channel counts. <br> **System capability:** SystemCapability.Multimedia.Audio.Device <br/>**Atomic service API:** This API can be used in atomic services since API version 12.|
| channelMasks<sup>9+</sup>     | Array&lt;number&gt;        | Yes   | No   | Supported channel masks. <br> **System capability:** SystemCapability.Multimedia.Audio.Device <br/>**Atomic service API:** This API can be used in atomic services since API version 12.|
| displayName<sup>10+</sup>     | string                     | Yes   | No   | Device display name. <br> **System capability:** SystemCapability.Multimedia.Audio.Device <br/>**Atomic service API:** This API can be used in atomic services since API version 12.|
| encodingTypes<sup>11+</sup>    | Array&lt;[AudioEncodingType](arkts-apis-audio-e.md#audioencodingtype8)&gt;                     | Yes   | Yes | Supported encoding types. <br> **System capability:** SystemCapability.Multimedia.Audio.Core <br/>**Atomic service API:** This API can be used in atomic services since API version 12.|
| spatializationSupported<sup>18+</sup>     | boolean                     | Yes   | Yes | Whether the device supports spatial audio. The value true means spatial audio is supported, and false means the opposite. <br> **System capability:** SystemCapability.Multimedia.Audio.Spatialization|
| model<sup>22+</sup>           | string                     | Yes   | Yes | Specific model category of the device.<br> **System capability:** SystemCapability.Multimedia.Audio.Device|
| capabilities<sup>22+</sup>    | Array&lt;[AudioStreamInfo](#audiostreaminfo8)&gt;| Yes   | Yes | Audio stream capabilities supported by the device.<br> **System capability:** SystemCapability.Multimedia.Audio.Device|

## AudioDevicePair

Describes an audio device pair used for foldback monitoring, including an input device and an output device.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Device

| Name              | Type                                              | Read-only | Optional | Description               |
| :---------------- | :------------------------------------------------ | :--- |---| :----------------- |
| inputDevice | [AudioDeviceDescriptor](#audiodevicedescriptor) | No | No | Description of the input audio device. |
| outputDevice | [AudioDeviceDescriptor](#audiodevicedescriptor) | No | No | Description of the output audio device. |

## VolumeEvent<sup>9+</sup>

Event received by the app when the volume changes.

**System capability:** SystemCapability.Multimedia.Audio.Volume

| Name       | Type                                | Read-only | Optional | Description                                        |
| ---------- | ----------------------------------- | ---- |---|-------------------------------------------|
| volumeType | [AudioVolumeType](arkts-apis-audio-e.md#audiovolumetype) | No | No | Audio volume type.                                    |
| volume     | number                              | No | No | Volume level. The settable range can be obtained by calling getMinVolume and getMaxVolume.  |
| updateUi   | boolean | No | No | Whether to display the system volume bar. The value true means the system volume bar is displayed, and false means the opposite.<br>If the app contains a custom volume bar, it is recommended to dynamically control its display based on this parameter: when updateUi is true, do not display the custom volume bar; when updateUi is false, display the custom volume bar. This avoids the issue where both the system volume bar and the app's custom volume bar are displayed or hidden simultaneously. |
| volumeMode<sup>19+</sup> | [AudioVolumeMode](arkts-apis-audio-e.md#audiovolumemode19) | No | Yes | Audio volume mode. The default value is SYSTEM_GLOBAL.|


## MicStateChangeEvent<sup>9+</sup>

Event received by the app when the microphone state changes.

**System capability:** SystemCapability.Multimedia.Audio.Device

| Name | Type | Read only | Optional | Description |
| ---------- | ----------------------------------- | ---- |---|-------------------------------------------------------- |
| mute | boolean | No | No | Whether the system microphone is muted. The value `true` means muted, and `false` means unmuted. |


## StreamVolumeEvent<sup>20+</sup>

Event received by the app when the audio stream volume changes.

**System capability:** SystemCapability.Multimedia.Audio.Volume

| Name       | Type                                | Read-only | Optional | Description                                                     |
| ---------- | ----------------------------------- | ---- |---|-------------------------------------------------------- |
| streamUsage | [StreamUsage](arkts-apis-audio-e.md#streamusage) | No | No | Audio stream whose volume changes.          |
| volume | number | No | No | Volume value.          |
| updateUi   | boolean | No | No | Whether to display the system volume bar. The value true means the system volume bar is displayed, and false means it is not displayed.<br>If the app contains a custom volume bar, it is recommended to dynamically control its display based on this parameter: when updateUi is true, the custom volume bar is not displayed; when updateUi is false, the custom volume bar is displayed. This avoids the issue where both the system volume bar and the app's custom volume bar are displayed or hidden simultaneously. |
| previousVolume<sup>23+</sup> | number | No | Yes | Volume value before the change. |

## DeviceChangeAction

Describes the device connection status change and device information.

**System capability:** SystemCapability.Multimedia.Audio.Device

| Name              | Type                                              | Read-only | Optional | Description               |
| :---------------- | :------------------------------------------------ | :-------- | :------- | :------------------------ |
| type              | [DeviceChangeType](arkts-apis-audio-e.md#devicechangetype)             | No  | No  | Device connection status change. |
| deviceDescriptors | [AudioDeviceDescriptors](arkts-apis-audio-t.md#audiodevicedescriptors) | No  | No  | Device information.         |

## AudioStreamDeviceChangeInfo<sup>11+</sup>

Event received by the app when the stream device changes.

**System capability:** SystemCapability.Multimedia.Audio.Device

| Name              | Type                                                                | Read Only | Optional | Description               |
| :---------------- |:------------------------------------------------------------------| :--- |---| :----------------- |
| devices              | [AudioDeviceDescriptors](arkts-apis-audio-t.md#audiodevicedescriptors)                 | No | No | Device Information.<br>**Atomic service API:** This API can be used in atomic services since API version 12. |
| changeReason | [AudioStreamDeviceChangeReason](arkts-apis-audio-e.md#audiostreamdevicechangereason11) | No | No | Stream device change reason.<br>**Atomic service API:** This API can be used in atomic services since API version 12. |
| preDevices | [AudioDeviceDescriptors](arkts-apis-audio-t.md#audiodevicedescriptors) | No | Yes | Device information before the app stream device change.<br>**Since:** 26.0.0<br>**Model restriction:** This API can be used only in the stage model.<br>**Atomic service API:** This API can be used in atomic services since API version 26.0.0. |

## CurrentOutputDeviceChangedEvent<sup>20+</sup>

Event indicating that the app receives an output device change.

**System capability:** SystemCapability.Multimedia.Audio.Core

| Name              | Type                                                                | Read Only | Optional | Description               |
| :---------------- |:------------------------------------------------------------------| :--- |---| :----------------- |
| devices              | [AudioDeviceDescriptors](arkts-apis-audio-t.md#audiodevicedescriptors)                 | No | No | Device Information. |
| changeReason | [AudioStreamDeviceChangeReason](arkts-apis-audio-e.md#audiostreamdevicechangereason11) | No | No | Device Change Reason. |
| recommendedAction | [OutputDeviceChangeRecommendedAction](arkts-apis-audio-e.md#outputdevicechangerecommendedaction20) | No | No | Recommended action after the device change. |
| preDevices | [AudioDeviceDescriptors](arkts-apis-audio-t.md#audiodevicedescriptors) | No | Yes | Device information before the app output device change.<br>**Since:** 26.0.0<br>**Model restriction:** This API can be used only in the stage model. |

## CurrentInputDeviceChangedEvent<sup>21+</sup>

Event received by the app when the input device changes.

**System capability:** SystemCapability.Multimedia.Audio.Core

| Name              | Type                                                                | Read-only | Optional | Description               |
| :---------------- |:------------------------------------------------------------------| :--- |---| :----------------- |
| devices              | [AudioDeviceDescriptors](arkts-apis-audio-t.md#audiodevicedescriptors)                 | No | No | Device information. |
| changeReason | [AudioStreamDeviceChangeReason](arkts-apis-audio-e.md#audiostreamdevicechangereason11) | No | No | Device change reason. |

## AudioTimestampInfo<sup>19+</sup>

Describes the audio stream timestamp and current data frame position information.

**System capability:** SystemCapability.Multimedia.Audio.Core

| Name | Type | Read-only | Optional | Description                                |
| ---------| ------ | ---- | ---- |-----------------------------------|
| framePos | number | Yes   | No   | Position of the current data frame being played or recorded.                   |
| timestamp | number | Yes   | No   | Timestamp when the current data frame position is reached during playback or recording, in nanoseconds. |

## AudioCapturerInfo<sup>8+</sup>

Describes audio capturer information.

**System capability:** SystemCapability.Multimedia.Audio.Core

| Name          | Type                      | Read-only | Optional | Description             |
| :------------ | :------------------------ | :--- |---| :--------------- |
| source        | [SourceType](arkts-apis-audio-e.md#sourcetype8) | No | No | Audio source type.       |
| capturerFlags | number                    | No | No | Capture stream behavior flag.<br>Set this to 0. |

## AudioCapturerOptions<sup>8+</sup>

Describes the audio capturer options.

| Name                                | Type                                                      | Read-only | Optional | Description                                                         |
| ----------------------------------- | --------------------------------------------------------- | --------- | -------- | ------------------------------------------------------------ |
| streamInfo                          | [AudioStreamInfo](#audiostreaminfo8)                      | No | No | Audio stream information.<br>**System capability:** SystemCapability.Multimedia.Audio.Capturer   |
| capturerInfo                        | [AudioCapturerInfo](#audiocapturerinfo8)                   | No | No | Audio capturer information.<br>**System capability:** SystemCapability.Multimedia.Audio.Capturer        |
| playbackCaptureConfig<sup>(deprecated)</sup> | [AudioPlaybackCaptureConfig](#audioplaybackcaptureconfigdeprecated) | No | Yes | Configuration of audio playback capture.<br>**System capability:** SystemCapability.Multimedia.Audio.PlaybackCapture<br>Supported since API version 10 and deprecated since API version 12. You are advised to use the [screen recording interface AVScreenCapture](../apis-media-kit/capi-avscreencapture.md) instead.  |
| playbackCaptureMode | [AudioPlaybackCaptureMode](arkts-apis-audio-e.md#audioplaybackcapturemode) | No | Yes | Playback capture mode. It can be set to an enum value in AudioPlaybackCaptureMode or a bitwise OR combination thereof. Currently, only MODE_DEFAULT (0x0), MODE_MEDIA (0x1), MODE_EXCLUDING_SELF (0x8000), and the bitwise OR combination of MODE_MEDIA and MODE_EXCLUDING_SELF (0x8001) are supported.<br>**Since:** 26.0.0<br>**Model restriction:** This API can be used only in the stage model.<br>**System capability:** SystemCapability.Multimedia.Audio.PlaybackCapture |

## AudioInterrupt<sup>(deprecated)</sup>

Parameters passed in for the audio interruption event.

> **NOTE**
>
> This is supported since API version 7 and deprecated since API version 9. No substitute API is provided.

**System capability:** SystemCapability.Multimedia.Audio.Renderer

| Name            | Type                                                        | Read-only | Optional | Description                                                  |
| --------------- | ----------------------------------------------------------- | --------- | -------- | ------------------------------------------------------------ |
| streamUsage     | [StreamUsage](arkts-apis-audio-e.md#streamusage)            | No        | No       | Audio stream usage type.                                     |
| contentType     | [ContentType](arkts-apis-audio-e.md#contenttypedeprecated)  | No        | No       | Audio interruption media type.                               |
| pauseWhenDucked | boolean                                                     | No        | No       | Whether to pause audio playback during an audio interruption. The value **true** means that audio playback can be paused during an audio interruption, and **false** means the opposite. |

## CaptureFilterOptions<sup>(deprecated)</sup>

Defines the filter criteria for the playback audio streams to be captured.

> **NOTE**
> This API is supported since API version 10 and deprecated since API version 12. You are advised to use the [Screen Recording Interface AVScreenCapture](../apis-media-kit/capi-avscreencapture.md) instead.

**System capability:** SystemCapability.Multimedia.Audio.PlaybackCapture

| Name   | Type                               | Read-only | Optional | Description                                                         |
| ------ | ---------------------------------- | ---- |---| ------------------------------------------------------------ |
| usages | Array\<[StreamUsage](arkts-apis-audio-e.md#streamusage)> | No | No | Specifies the StreamUsage types of the playback audio streams to be captured. Zero or more StreamUsage types can be specified simultaneously. When the array is empty, by default, playback audio streams with StreamUsage of STREAM_USAGE_MUSIC, STREAM_USAGE_MOVIE, STREAM_USAGE_GAME, and STREAM_USAGE_AUDIOBOOK are captured.<br>In API version 10, CaptureFilterOptions supports the use of StreamUsage.STREAM_USAGE_VOICE_COMMUNICATION, which requires the ohos.permission.CAPTURE_VOICE_DOWNLINK_AUDIO permission. This permission can be requested only by system apps.<br>Since API version 11, CaptureFilterOptions no longer supports StreamUsage.STREAM_USAGE_VOICE_COMMUNICATION, so this permission is no longer involved in this API. |

## AudioPlaybackCaptureConfig<sup>(deprecated)</sup>

Configuration information for audio playback capture.

> **NOTE**
> Supported since API version 10 and deprecated since API version 12. You are advised to use [Screen Recording Interface AVScreenCapture](../apis-media-kit/capi-avscreencapture.md) instead.

**System capability:** SystemCapability.Multimedia.Audio.PlaybackCapture

| Name          | Type                                          | Read-only | Optional | Description                             |
| ------------- | --------------------------------------------- | --------- | -------- | --------------------------------------- |
| filterOptions | [CaptureFilterOptions](#capturefilteroptionsdeprecated) | No        | No       | Filtering information for the playback audio streams to be captured. |

## InterruptAction<sup>(deprecated)</sup>

Callback for the audio interruption/focus acquisition event.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 9. You are advised to use [InterruptEvent](#interruptevent9) instead.

**System capability:** SystemCapability.Multimedia.Audio.Renderer

| Name       | Type                                        | Read-only | Optional | Description                                                         |
| ---------- | ------------------------------------------- | --------- | -------- | ------------------------------------------------------------ |
| actionType | [InterruptActionType](arkts-apis-audio-e.md#interruptactiontypedeprecated) | No  | No  | Event return type. TYPE_ACTIVATED indicates a focus trigger event, and TYPE_INTERRUPT indicates an audio interruption event. |
| type       | [InterruptType](arkts-apis-audio-e.md#interrupttype)             | No  | Yes | Interruption event type.                                               |
| hint       | [InterruptHint](arkts-apis-audio-e.md#interrupthint)             | No  | Yes | Interruption event hint.                                               |
| activated  | boolean                                     | No  | Yes | Whether the focus is acquired or released successfully. The value **true** indicates that the focus is acquired or released successfully, and **false** indicates the opposite. |

## SystemRecordControllerConfig

Defines the configuration information of the system recording control panel.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Multimedia.Audio.Capturer

| Name | Type | Read-only | Optional | Description |
| :---- | :---- | :---- | :---- | :---- |
| sourceType | [SourceType](arkts-apis-audio-e.md#sourcetype8) | No | No | Audio source type that the app intends to use. Based on this parameter, the system determines the recording scenario of the app and provides the user with a matching noise reduction mode selection capability. Supported audio source types include SOURCE_TYPE_MIC, SOURCE_TYPE_CAMCORDER, and SOURCE_TYPE_LIVE. |