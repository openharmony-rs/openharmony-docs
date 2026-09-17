# @ohos.multimedia.audio(Audio Renderer, Capturer And Management)

The module provides basic audio control capabilities, including volume adjustment, device management, data capture, and rendering.

This module provides the following common audio-related functions:

- [AudioManager](arkts-audio-multimedia-audio.md): audio manager.  
- [AudioRenderer](arkts-audio-multimedia-audio.md): audio renderer, used to play Pulse Code Modulation (PCM) audio  
data.  
- [AudioCapturer](arkts-audio-multimedia-audio.md): audio capturer, used to record PCM audio data.

**Since:** 7

**System capability:** 
- API version 12 and later: SystemCapability.Multimedia.Audio.Core

## Modules to Import

```TypeScript
import { audio } from '@kit.AudioKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [createAudioCapturer](arkts-audio-audio-createaudiocapturer-f.md) | Creates an AudioCapturer instance. This API uses an asynchronous callback to return the result. |
| [createAudioCapturer](arkts-audio-audio-createaudiocapturer-f.md) | Creates an AudioCapturer instance. This API uses a promise to return the result. |
| [createAudioLoopback](arkts-audio-audio-createaudioloopback-f.md) | Creates an &lt;b&gt;AudioLoopback&lt;/b&gt; instance, which provides low-latency in-ear monitoring using a fast capturer and renderer. |
| [createAudioRenderer](arkts-audio-audio-createaudiorenderer-f.md) | Obtains an [AudioRenderer](arkts-audio-audio-audiorenderer-i.md) instance. This method uses a promise to return the renderer instance. |
| [createAudioRenderer](arkts-audio-audio-createaudiorenderer-f.md) | Obtains an [AudioRenderer](arkts-audio-audio-audiorenderer-i.md) instance. This method uses a promise to return the renderer instance. |
| [getAudioManager](arkts-audio-audio-getaudiomanager-f.md) | Obtains an AudioManager instance. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [createAsrProcessingController](arkts-audio-audio-createasrprocessingcontroller-f-sys.md) | Create ASR processing controller on one audio capturer. |
| [createGlobalAudioLoopback](arkts-audio-audio-createglobalaudioloopback-f-sys.md) | Creates a global audio loopback instance, which provides low-latency in-ear monitor function. Hardware audio loopback can only be created in supported platform, application can use [isAudioLoopbackSupported](arkts-audio-audio-audiostreammanager-i.md#isaudioloopbacksupported) to check first. There should be only one main instance that own the global loopback in the system, the others are controllers. A controller can manage the global loopback by sending commands to the main instance, and listen status change from it. |
| [createMicInAudioCapturer](arkts-audio-audio-createmicinaudiocapturer-f-sys.md) | Obtains a special [AudioCapturer](arkts-audio-audio-audiocapturer-i.md) instance. This method uses a promise to return the capturer instance. This capture can be used to record both Mic-In audio data and echo reference signal, for application to process algorithm. Mic-In audio data and echo reference signal will be put in one buffer or multiple buffers according to configuration set by application. Capturer is also not allowed to be created when application is in background. |
| [createTonePlayer](arkts-audio-audio-createtoneplayer-f-sys.md) | Obtains a [TonePlayer](arkts-audio-audio-toneplayer-i-sys.md) instance. This method uses an asynchronous callback to return the renderer instance. |
| [createTonePlayer](arkts-audio-audio-createtoneplayer-f-sys.md) | Obtains a [TonePlayer](arkts-audio-audio-toneplayer-i-sys.md) instance. This method uses a promise to return the renderer instance. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [AudioCapturer](arkts-audio-audio-audiocapturer-i.md) | This interface provides APIs for audio capture. |
| [AudioCapturerChangeInfo](arkts-audio-audio-audiocapturerchangeinfo-i.md) | Describes the audio capturer change event. |
| [AudioCapturerInfo](arkts-audio-audio-audiocapturerinfo-i.md) | Describes audio capturer information. |
| [AudioCapturerOptions](arkts-audio-audio-audiocaptureroptions-i.md) | Describes audio capturer configurations. |
| [AudioDebuggingManager](arkts-audio-audio-audiodebuggingmanager-i.md) | Provides audio debug management capabilities. |
| [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | Describes an audio device. |
| [AudioDeviceEnhanceManager](arkts-audio-audio-audiodeviceenhancemanager-i.md) | Provides enhanced audio device management capabilities. |
| [AudioDevicePair](arkts-audio-audio-audiodevicepair-i.md) | Describes an audio device pair including both input and output devices. |
| [AudioInterrupt](arkts-audio-audio-audiointerrupt-i.md) | Describes input parameters of audio interruption events. |
| [AudioLoopback](arkts-audio-audio-audioloopback-i.md) | This interface provides APIs for audio monitoring. |
| [AudioManager](arkts-audio-audio-audiomanager-i.md) | This interface implements audio volume and device management. |
| [AudioPlaybackCaptureConfig](arkts-audio-audio-audioplaybackcaptureconfig-i.md) | Defines configuration for capturing played audio. |
| [AudioRecordingManager](arkts-audio-audio-audiorecordingmanager-i.md) | Provides recording strategy management, including collaborative recording and recording control capabilities. |
| [AudioRenderer](arkts-audio-audio-audiorenderer-i.md) | This interface provides APIs for audio rendering. |
| [AudioRendererChangeInfo](arkts-audio-audio-audiorendererchangeinfo-i.md) | Describes the audio renderer change event. |
| [AudioRendererInfo](arkts-audio-audio-audiorendererinfo-i.md) | Describes audio renderer information. |
| [AudioRendererOptions](arkts-audio-audio-audiorendereroptions-i.md) | Describes audio renderer configurations. |
| [AudioRoutingManager](arkts-audio-audio-audioroutingmanager-i.md) | This interface implements audio routing management. |
| [AudioSessionDeactivatedEvent](arkts-audio-audio-audiosessiondeactivatedevent-i.md) | Describes the event indicating that an audio session is deactivated. |
| [AudioSessionManager](arkts-audio-audio-audiosessionmanager-i.md) | This interface implements audio session management. |
| [AudioSessionStateChangedEvent](arkts-audio-audio-audiosessionstatechangedevent-i.md) | Describes the event indicating that the audio session state changes. |
| [AudioSessionStrategy](arkts-audio-audio-audiosessionstrategy-i.md) | Describes an audio session strategy. |
| [AudioSpatializationManager](arkts-audio-audio-audiospatializationmanager-i.md) | Implements audio spatialization management. @typedef AudioSpatializationManager This interface implements spatial audio management. |
| [AudioStreamDeviceChangeInfo](arkts-audio-audio-audiostreamdevicechangeinfo-i.md) | Describes the event received by the application when the audio stream device is changed. |
| [AudioStreamInfo](arkts-audio-audio-audiostreaminfo-i.md) | Describes audio stream information. |
| [AudioStreamManager](arkts-audio-audio-audiostreammanager-i.md) | This interface implements audio stream management. |
| [AudioTimestampInfo](arkts-audio-audio-audiotimestampinfo-i.md) | Describes the information about the audio stream timestamp and the current data frame position. |
| [AudioVolumeGroupManager](arkts-audio-audio-audiovolumegroupmanager-i.md) | This interface implements volume management for an audio group. |
| [AudioVolumeManager](arkts-audio-audio-audiovolumemanager-i.md) | This interface implements audio volume management. |
| [CaptureFilterOptions](arkts-audio-audio-capturefilteroptions-i.md) | Defines the options for filtering the played audio streams to be recorded. |
| [CurrentInputDeviceChangedEvent](arkts-audio-audio-currentinputdevicechangedevent-i.md) | Describes the event indicating that the input device changes. |
| [CurrentOutputDeviceChangedEvent](arkts-audio-audio-currentoutputdevicechangedevent-i.md) | Describes the event indicating that the output device changes. |
| [DeviceBlockStatusInfo](arkts-audio-audio-deviceblockstatusinfo-i.md) | Describes the audio device blocked status and device information. |
| [DeviceChangeAction](arkts-audio-audio-devicechangeaction-i.md) | Describes the device connection status and device information. |
| [InterruptAction](arkts-audio-audio-interruptaction-i.md) | Describes the callback invoked for audio interruption or focus gain events.When the audio of an application is interrupted by another application, the callback is invoked to notify the former application. |
| [InterruptEvent](arkts-audio-audio-interruptevent-i.md) | Describes the interruption event received by the application when the audio is interrupted. |
| [MicStateChangeEvent](arkts-audio-audio-micstatechangeevent-i.md) | Describes the event received by the application when the microphone mute status is changed. |
| [StreamVolumeEvent](arkts-audio-audio-streamvolumeevent-i.md) | Describes the event received by the application when the audio stream volume is changed. |
| [SystemRecordControllerConfig](arkts-audio-audio-systemrecordcontrollerconfig-i.md) | Defines the configuration for the system recording controller panel. |
| [VolumeEvent](arkts-audio-audio-volumeevent-i.md) | Describes the event received by the application when the volume is changed. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [ActiveStreamVolumeInfo](arkts-audio-audio-activestreamvolumeinfo-i-sys.md) | Volume information for active audio streams. |
| [AppIdInfo](arkts-audio-audio-appidinfo-i-sys.md) | Describes app ID information. |
| [AsrProcessingController](arkts-audio-audio-asrprocessingcontroller-i-sys.md) | ASR processing controller. |
| [AudioCapturer](arkts-audio-audio-audiocapturer-i-sys.md) | This interface provides APIs for audio capture. |
| [AudioCapturerChangeInfo](arkts-audio-audio-audiocapturerchangeinfo-i-sys.md) | Describes the audio capturer change event. |
| [AudioCapturerFilter](arkts-audio-audio-audiocapturerfilter-i-sys.md) | Describe audio capturer filter. |
| [AudioCapturerMicInConfig](arkts-audio-audio-audiocapturermicinconfig-i-sys.md) | Describes audio capturer configuration that can capture microphone input (mic-in) audio data before any processing. |
| [AudioCapturerMicInData](arkts-audio-audio-audiocapturermicindata-i-sys.md) | Describes audio capturer data that contains processed audio data and microphone input (mic-in) audio data before any processing. |
| [AudioCapturerOptions](arkts-audio-audio-audiocaptureroptions-i-sys.md) | Describes audio capturer configurations. |
| [AudioCollaborativeManager](arkts-audio-audio-audiocollaborativemanager-i-sys.md) | Implements audio collaborative management. |
| [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i-sys.md) | Describes an audio device. |
| [AudioDeviceEnhanceManager](arkts-audio-audio-audiodeviceenhancemanager-i-sys.md) | Provides enhanced audio device management capabilities. |
| [AudioEffectManager](arkts-audio-audio-audioeffectmanager-i-sys.md) | Implements audio effect management. @typedef AudioEffectManager |
| [AudioEffectProperty](arkts-audio-audio-audioeffectproperty-i-sys.md) | Describes an audio effect property. |
| [AudioHRTFAnonymousDescriptor](arkts-audio-audio-audiohrtfanonymousdescriptor-i-sys.md) | Anonymous personalzied HRTF file descriptor for cross-process transfer. |
| [AudioManager](arkts-audio-audio-audiomanager-i-sys.md) | This interface implements audio volume and device management. |
| [AudioPersonalizedSpatialEnabledChangeForAnyDevice](arkts-audio-audio-audiopersonalizedspatialenabledchangeforanydevice-i-sys.md) | This interface is used to notify the listener of personalized spatialization enabled state change of any device. |
| [AudioRecordingManager](arkts-audio-audio-audiorecordingmanager-i-sys.md) | Provides recording strategy management, including collaborative recording and recording control capabilities. |
| [AudioRenderer](arkts-audio-audio-audiorenderer-i-sys.md) | This interface provides APIs for audio rendering. |
| [AudioRendererChangeInfo](arkts-audio-audio-audiorendererchangeinfo-i-sys.md) | Describes the audio renderer change event. |
| [AudioRendererFilter](arkts-audio-audio-audiorendererfilter-i-sys.md) | Describes audio renderer filter. |
| [AudioRendererOptions](arkts-audio-audio-audiorendereroptions-i-sys.md) | Describes audio renderer configurations. |
| [AudioRendererTargetParams](arkts-audio-audio-audiorenderertargetparams-i-sys.md) | Options for setting the render target of an audio renderer. This parameter takes effect only when the target is non-PLAYBACK. In other cases, this parameter does not need to be specified and does not take effect even if specified. Both uid and streamId must be specified. |
| [AudioRoutingManager](arkts-audio-audio-audioroutingmanager-i-sys.md) | This interface implements audio routing management. |
| [AudioSpatialDeviceState](arkts-audio-audio-audiospatialdevicestate-i-sys.md) | Describes spatial device state. |
| [AudioSpatialEnabledStateForDevice](arkts-audio-audio-audiospatialenabledstatefordevice-i-sys.md) | This interface is used to notify the listener of any device Spatialization or Head Tracking enable or Adaptive Spatial Rendering state change. |
| [AudioSpatializationManager](arkts-audio-audio-audiospatializationmanager-i-sys.md) | Implements audio spatialization management. @typedef AudioSpatializationManager This interface implements spatial audio management. |
| [AudioVolumeGroupManager](arkts-audio-audio-audiovolumegroupmanager-i-sys.md) | This interface implements volume management for an audio group. |
| [AudioVolumeManager](arkts-audio-audio-audiovolumemanager-i-sys.md) | This interface implements audio volume management. |
| [InterruptResult](arkts-audio-audio-interruptresult-i-sys.md) | Describes audio interrupt operation results. |
| [SoundCardInfo](arkts-audio-audio-soundcardinfo-i-sys.md) | Describes sound card information. |
| [SystemRecordControllerChangeInfo](arkts-audio-audio-systemrecordcontrollerchangeinfo-i-sys.md) | Defines the information carried when the system recording controller state changes. It includes the enable status, application UID and expected audio source type. |
| [SystemVolumeFilter](arkts-audio-audio-systemvolumefilter-i-sys.md) | Describes the system volume filter. |
| [TonePlayer](arkts-audio-audio-toneplayer-i-sys.md) | Provides APIs for tone playing. |
| [VolumeEvent](arkts-audio-audio-volumeevent-i-sys.md) | Describes the event received by the application when the volume is changed. |
| [VolumeGroupInfo](arkts-audio-audio-volumegroupinfo-i-sys.md) | Describes an audio volume group. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [ActiveDeviceType](arkts-audio-audio-activedevicetype-e.md) | Enumerates the active device types. |
| [AudioChannel](arkts-audio-audio-audiochannel-e.md) | Enumerates the audio channels. |
| [AudioChannelLayout](arkts-audio-audio-audiochannellayout-e.md) | Audio AudioChannel Layout. A 64-bit integer indicates that the appearance and order of the speakers for recording or playback. |
| [AudioConcurrencyMode](arkts-audio-audio-audioconcurrencymode-e.md) | Enumerates the audio concurrency modes. |
| [AudioDataCallbackResult](arkts-audio-audio-audiodatacallbackresult-e.md) | Enumerates the audio data callback results. |
| [AudioEffectMode](arkts-audio-audio-audioeffectmode-e.md) | Enumerates the audio effect modes. |
| [AudioEncodingType](arkts-audio-audio-audioencodingtype-e.md) | Enumerates the audio encoding types. |
| [AudioErrors](arkts-audio-audio-audioerrors-e.md) | Enumerates the error codes available for audio management. |
| [AudioLatencyType](arkts-audio-audio-audiolatencytype-e.md) | Enumerates the audio latency types. |
| [AudioLoopbackEqualizerPreset](arkts-audio-audio-audioloopbackequalizerpreset-e.md) | Enumerates the equalizer types of audio loopback. |
| [AudioLoopbackMode](arkts-audio-audio-audioloopbackmode-e.md) | Enumerates the audio loopback modes. |
| [AudioLoopbackReverbPreset](arkts-audio-audio-audioloopbackreverbpreset-e.md) | Enumerates the reverb modes of audio loopback. |
| [AudioLoopbackStatus](arkts-audio-audio-audioloopbackstatus-e.md) | Enumerates the audio loopback statuses. |
| [AudioPlaybackCaptureMode](arkts-audio-audio-audioplaybackcapturemode-e.md) | Defines mode for playback capture, each mode means different target streams to capture. |
| [AudioPrivacyType](arkts-audio-audio-audioprivacytype-e.md) | Enumerates whether an audio stream can be recorded by other applications. |
| [AudioRendererRate](arkts-audio-audio-audiorendererrate-e.md) | Enumerates the audio renderer rates. |
| [AudioRingMode](arkts-audio-audio-audioringmode-e.md) | Enumerates the audio ring modes. |
| [AudioSampleFormat](arkts-audio-audio-audiosampleformat-e.md) | Enumerates the audio sample formats. |
| [AudioSamplingRate](arkts-audio-audio-audiosamplingrate-e.md) | Enumerates the audio sampling rates. The sampling rates supported vary according to the device in use. |
| [AudioScene](arkts-audio-audio-audioscene-e.md) | Enumerates the audio scenes. |
| [AudioSessionBehaviorFlags](arkts-audio-audio-audiosessionbehaviorflags-e.md) | Enumerates audio session behavior flags. |
| [AudioSessionDeactivatedReason](arkts-audio-audio-audiosessiondeactivatedreason-e.md) | Enumerates the reasons for deactivating an audio session. |
| [AudioSessionScene](arkts-audio-audio-audiosessionscene-e.md) | Enumerates the audio session scenes. |
| [AudioSessionStateChangeHint](arkts-audio-audio-audiosessionstatechangehint-e.md) | Enumerates the hints for audio session state changes. |
| [AudioState](arkts-audio-audio-audiostate-e.md) | Enumerates the audio states. |
| [AudioStreamDeviceChangeReason](arkts-audio-audio-audiostreamdevicechangereason-e.md) | Enumerates the reasons for audio stream device changes. |
| [AudioVolumeMode](arkts-audio-audio-audiovolumemode-e.md) | Enumerates the audio volume modes. |
| [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | Enumerates the audio volume types. |
| [BluetoothAndNearlinkPreferredRecordCategory](arkts-audio-audio-bluetoothandnearlinkpreferredrecordcategory-e.md) | Enumerates the preferred device categories available for recording with Bluetooth or NearLink. |
| [ChannelBlendMode](arkts-audio-audio-channelblendmode-e.md) | Enumerates the audio channel blending modes. |
| [CommunicationDeviceType](arkts-audio-audio-communicationdevicetype-e.md) | Enumerates the available device types for communication. @enum { int } |
| [ContentType](arkts-audio-audio-contenttype-e.md) | Enumerates the audio content types. |
| [DeviceBlockStatus](arkts-audio-audio-deviceblockstatus-e.md) | Enumerates the blocked statuses of audio devices. |
| [DeviceChangeType](arkts-audio-audio-devicechangetype-e.md) | Enumerates the device connection statuses. |
| [DeviceFlag](arkts-audio-audio-deviceflag-e.md) | Enumerates the audio device flags. |
| [DeviceRole](arkts-audio-audio-devicerole-e.md) | Enumerates the device roles. |
| [DeviceType](arkts-audio-audio-devicetype-e.md) | Enumerates the device types. |
| [DeviceUsage](arkts-audio-audio-deviceusage-e.md) | Enumerates the audio device types by usage. |
| [InterruptActionType](arkts-audio-audio-interruptactiontype-e.md) | Enumerates the returned event types for audio interruption events. |
| [InterruptForceType](arkts-audio-audio-interruptforcetype-e.md) | Enumerates the types of force that causes audio interruption. |
| [InterruptHint](arkts-audio-audio-interrupthint-e.md) | Enumerates the hints provided along with audio interruption. |
| [InterruptMode](arkts-audio-audio-interruptmode-e.md) | Enumerates the audio interruption modes. |
| [InterruptType](arkts-audio-audio-interrupttype-e.md) | Enumerates the audio interruption types. |
| [NoiseReductionMode](arkts-audio-audio-noisereductionmode-e.md) | Enumerates the noise reduction modes. |
| [OutputDeviceChangeRecommendedAction](arkts-audio-audio-outputdevicechangerecommendedaction-e.md) | Enumerates the recommended actions to take after an output device changes. |
| [PlaybackCaptureStartState](arkts-audio-audio-playbackcapturestartstate-e.md) | Defines the playback capture start state, which is returned asynchronously after calling [requestPlaybackCaptureStart](arkts-audio-audio-audiocapturer-i.md#requestplaybackcapturestart) function. |
| [SourceType](arkts-audio-audio-sourcetype-e.md) | Enumerates the types of audio streams captured. |
| [StreamUsage](arkts-audio-audio-streamusage-e.md) | Enumerates the types of audio streams played. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [AsrAecMode](arkts-audio-audio-asraecmode-e-sys.md) | ASR AEC mode. |
| [AsrNoiseSuppressionMode](arkts-audio-audio-asrnoisesuppressionmode-e-sys.md) | ASR noise suppression mode. |
| [AsrVoiceControlMode](arkts-audio-audio-asrvoicecontrolmode-e-sys.md) | ASR voice control mode. |
| [AsrVoiceMuteMode](arkts-audio-audio-asrvoicemutemode-e-sys.md) | ASR voice mute mode. |
| [AsrWhisperDetectionMode](arkts-audio-audio-asrwhisperdetectionmode-e-sys.md) | ASR whisper detection mode. |
| [AudioDevcieSelectStrategy](arkts-audio-audio-audiodevcieselectstrategy-e-sys.md) | Enumerates the device select strategy. |
| [AudioPlaybackCaptureMode](arkts-audio-audio-audioplaybackcapturemode-e-sys.md) | Defines mode for playback capture, each mode means different target streams to capture. |
| [AudioSeparationVolumeType](arkts-audio-audio-audioseparationvolumetype-e-sys.md) | Volume type for audio separation effect. |
| [AudioSessionBehaviorFlags](arkts-audio-audio-audiosessionbehaviorflags-e-sys.md) | Enumerates audio session behavior flags. |
| [AudioSpatialDeviceType](arkts-audio-audio-audiospatialdevicetype-e-sys.md) | Describes a spatial device type group. |
| [AudioSpatializationSceneType](arkts-audio-audio-audiospatializationscenetype-e-sys.md) | Describes a spatialization scene type group. |
| [AudioVolumeType](arkts-audio-audio-audiovolumetype-e-sys.md) | Enumerates the audio volume types. |
| [ConnectType](arkts-audio-audio-connecttype-e-sys.md) | Connect type for device. |
| [DeviceFlag](arkts-audio-audio-deviceflag-e-sys.md) | Enumerates the audio device flags. |
| [DeviceType](arkts-audio-audio-devicetype-e-sys.md) | Enumerates the device types. |
| [EffectFlag](arkts-audio-audio-effectflag-e-sys.md) | Enumerates audio effect flags. |
| [InterruptRequestResultType](arkts-audio-audio-interruptrequestresulttype-e-sys.md) | Enumerates audio interrupt request result type. |
| [InterruptRequestType](arkts-audio-audio-interruptrequesttype-e-sys.md) | Enumerates the audio interrupt request type. |
| [PolicyType](arkts-audio-audio-policytype-e-sys.md) | Enumerates type. |
| [RenderTarget](arkts-audio-audio-rendertarget-e-sys.md) | Audio render target. |
| [SourceType](arkts-audio-audio-sourcetype-e-sys.md) | Enumerates the types of audio streams captured. |
| [SpatialAudioSourceType](arkts-audio-audio-spatialaudiosourcetype-e-sys.md) | Enumerates the spatial audio source type. |
| [StreamUsage](arkts-audio-audio-streamusage-e-sys.md) | Enumerates the types of audio streams played. |
| [ToneType](arkts-audio-audio-tonetype-e-sys.md) | Enumerates tone types for player. |
| [VolumeAdjustType](arkts-audio-audio-volumeadjusttype-e-sys.md) | Enumerates volume adjustment types. |
| [VolumeFlag](arkts-audio-audio-volumeflag-e-sys.md) | Enumerates volume related operations. Flags should be powers of 2! |
<!--DelEnd-->

### Types

| Name | Description |
| --- | --- |
| [AudioCapturerChangeInfoArray](arkts-audio-audio-audiocapturerchangeinfoarray-t.md) | Defines an AudioCapturerChangeInfo array, which is read-only. |
| [AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md) | Defines an [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) array, which is read- only. |
| [AudioEffectInfoArray](arkts-audio-audio-audioeffectinfoarray-t.md) | Defines an array that contains the audio effect mode corresponding to a specific audio content type (specified by **ContentType**) and audio stream usage (specified by **StreamUsage**). The [AudioEffectMode](arkts-audio-audio-audioeffectmode-e.md) array is read-only. |
| [AudioRendererChangeInfoArray](arkts-audio-audio-audiorendererchangeinfoarray-t.md) | Defines an AudioRendererChangeInfo array, which is read-only. |
| [AudioRendererWriteDataCallback](arkts-audio-audio-audiorendererwritedatacallback-t.md) | Defines the callback function used to write data to the audio renderer. Once the callback function finishes its execution, the audio service queues the data pointed to by **data** for playback. Therefore, do not change the data outside the callback. It is crucial to fill **data** with the exact length of data designated for playback; otherwise, noises may occur during playback. |
| [DeviceTypeArray](arkts-audio-audio-devicetypearray-t.md) | Defines the device type array. |

<!--Del-->
### Types(System API)

| Name | Description |
| --- | --- |
| [ActiveStreamsVolumeInfoArray](arkts-audio-audio-activestreamsvolumeinfoarray-t-sys.md) | ActiveStreamVolumeInfo array. |
| [StreamUsageArray](arkts-audio-audio-streamusagearray-t-sys.md) | Array of StreamUsages. |
| [VolumeGroupInfos](arkts-audio-audio-volumegroupinfos-t-sys.md) | Array of VolumeGroupInfos, which is read-only. |
<!--DelEnd-->

### Constants

| Name | Description |
| --- | --- |
| [DEFAULT_INTERRUPT_GROUP_ID](arkts-audio-audio-con.md#default_interrupt_group_id) | Define default interrupt group id for audio. |
| [DEFAULT_VOLUME_GROUP_ID](arkts-audio-audio-con.md#default_volume_group_id) | Define default volume group id for audio. |

<!--Del-->
### Constants(System API)

| Name | Description |
| --- | --- |
| [LOCAL_NETWORK_ID](arkts-audio-audio-con-sys.md#local_network_id) | Define local device network id for audio. |
<!--DelEnd-->
