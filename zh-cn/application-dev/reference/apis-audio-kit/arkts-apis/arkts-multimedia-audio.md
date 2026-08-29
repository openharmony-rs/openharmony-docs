# @ohos.multimedia.audio

音频管理提供基础的音频控制能力，包括音量调节、设备管理、数据采集及渲染。 该模块提供以下音频相关的常用功能：  
- [AudioManager](arkts-audio-audio-audiomanager-i.md)：音频管理器。  
- [AudioDeviceEnhanceManager](arkts-audio-audio-audiodeviceenhancemanager-i.md)：音频设备增强管理器。  
- [AudioRenderer](arkts-audio-audio-audiorenderer-i.md)：音频渲染，用于播放PCM（Pulse Code Modulation）音频数据。  
- [AudioCapturer](arkts-audio-audio-audiocapturer-i.md)：音频采集，用于录制PCM音频数据。

**起始版本：** 7

**系统能力：** 
- API版本12+：SystemCapability.Multimedia.Audio.Core

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [createAudioCapturer](arkts-audio-audio-createaudiocapturer-f.md) | 获取音频采集器。使用callback异步回调。 |
| [createAudioCapturer](arkts-audio-audio-createaudiocapturer-f.md) | 获取音频采集器。使用Promise异步回调。 |
| [createAudioLoopback](arkts-audio-audio-createaudioloopback-f.md) | 创建音频返听器。使用Promise异步回调。 在使用createAudioLoopback接口之前，需先通过 [isAudioLoopbackSupported](arkts-audio-audio-audiostreammanager-i.md#isaudioloopbacksupported)查询系统返听能力。 |
| [createAudioRenderer](arkts-audio-audio-createaudiorenderer-f.md) | 获取音频渲染器。使用callback异步回调。 |
| [createAudioRenderer](arkts-audio-audio-createaudiorenderer-f.md) | 获取音频渲染器。使用Promise异步回调。 |
| [getAudioManager](arkts-audio-audio-getaudiomanager-f.md) | 获取音频管理器。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [createAsrProcessingController](arkts-audio-audio-createasrprocessingcontroller-f-sys.md) | 获取自动语音识别（ASR）处理控制器。 |
| [createGlobalAudioLoopback](arkts-audio-audio-createglobalaudioloopback-f-sys.md) | 创建一个全局音频返听实例，该实例提供低延迟的入耳监听功能。 硬件音频返听只能在支持的平台中创建，应用程序应首先使用[isAudioLoopbackSupported](arkts-audio-audio-audiostreammanager-i.md#isaudioloopbacksupported) 进行检查。 系统中只能存在一个拥有全局返听功能的主实例，其他实例均为控制器。控制器可以通过向主实例发送命令来管理全局返听，并监听其状态变化。 |
| [createMicInAudioCapturer](arkts-audio-audio-createmicinaudiocapturer-f-sys.md) | 获取音频采集器。使用Promise异步回调。 |
| [createTonePlayer](arkts-audio-audio-createtoneplayer-f-sys.md) | 创建DTMF播放器。使用callback异步回调。 |
| [createTonePlayer](arkts-audio-audio-createtoneplayer-f-sys.md) | 创建DTMF播放器。使用Promise异步回调。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [AudioCapturer](arkts-audio-audio-audiocapturer-i.md) | 提供音频采集的相关接口。在使用AudioCapturer的接口之前，需先通过 [createAudioCapturer](arkts-audio-audio-createaudiocapturer-f.md) 获取AudioCapturer实例。 |
| [AudioCapturerChangeInfo](arkts-audio-audio-audiocapturerchangeinfo-i.md) | 描述音频采集器更改信息。 |
| [AudioCapturerInfo](arkts-audio-audio-audiocapturerinfo-i.md) | 描述音频采集器信息。 |
| [AudioCapturerOptions](arkts-audio-audio-audiocaptureroptions-i.md) | 音频采集器选项信息。 |
| [AudioDebuggingManager](arkts-audio-audio-audiodebuggingmanager-i.md) | 音频调试管理器，用于音频运行时调试，包括获取快照信息等功能，用于定位音频播放、录音、耳返、会话等场景中的异常问题。 **起始版本：** 26.0.0 |
| [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md) | 描述音频设备。 |
| [AudioDeviceEnhanceManager](arkts-audio-audio-audiodeviceenhancemanager-i.md) | 音频设备增强管理功能，用于应用级音频设备选择及流维度音频设备选择。 在使用AudioDeviceEnhanceManager的接口之前，需要先通过getDeviceEnhanceManager获取AudioDeviceEnhanceManager实例。 |
| [AudioDevicePair](arkts-audio-audio-audiodevicepair-i.md) | 描述返听使用的音频设备对，包含输入设备和输出设备。 |
| [AudioInterrupt](arkts-audio-audio-audiointerrupt-i.md) | 音频监听事件传入的参数。 |
| [AudioLoopback](arkts-audio-audio-audioloopback-i.md) | 提供音频返听的相关接口。 在使用AudioLoopback的接口之前，需先通过 [audio.createAudioLoopback](arkts-audio-audio-createaudioloopback-f.md)获取 AudioLoopback实例。 当启用音频返听时，系统会创建低时延渲染器与低时延采集器，实现低时延耳返功能。采集的音频直接通过内部路由返回到渲染器。对于渲染器，其音频焦点策略与 [STREAM_USAGE_MUSIC](arkts-audio-audio-streamusage-e.md)相匹配。对于采集器，其音频焦点策略与 [SOURCE_TYPE_MIC](arkts-audio-audio-sourcetype-e.md)相匹配。 输入/输出设备由系统自动选择。如果当前输入/输出不支持低时延，则音频返听无法启用。在运行过程中，如果音频焦点被另一个音频流抢占，输入/输出设备切换到不支持低时延的设备，系统会自动禁用音频返听。 |
| [AudioManager](arkts-audio-audio-audiomanager-i.md) | 管理音频音量和音频设备。在调用AudioManager的接口前，需要先通过[getAudioManager](arkts-audio-audio-getaudiomanager-f.md)创建实例。 |
| [AudioPlaybackCaptureConfig](arkts-audio-audio-audioplaybackcaptureconfig-i.md) | 音频内录的配置信息。 |
| [AudioRecordingManager](arkts-audio-audio-audiorecordingmanager-i.md) | 录音策略管理，提供协同录音和录音控制能力。 在使用AudioRecordingManager的接口之前，需先通过 getRecordingManager获取AudioRecordingManager实例 。 |
| [AudioRenderer](arkts-audio-audio-audiorenderer-i.md) | 音频渲染。在使用AudioRenderer的接口之前，需先通过 [audio.createAudioRenderer](arkts-audio-audio-createaudiorenderer-f.md) 获取AudioRenderer实例。 |
| [AudioRendererChangeInfo](arkts-audio-audio-audiorendererchangeinfo-i.md) | 描述音频渲染器更改信息。 |
| [AudioRendererInfo](arkts-audio-audio-audiorendererinfo-i.md) | 音频渲染器信息。 |
| [AudioRendererOptions](arkts-audio-audio-audiorendereroptions-i.md) | 音频渲染器选项信息。 |
| [AudioRoutingManager](arkts-audio-audio-audioroutingmanager-i.md) | 音频路由管理。在使用AudioRoutingManager的接口前，需要使用 [getRoutingManager](arkts-audio-audio-audiomanager-i.md#getroutingmanager)获取AudioRoutingManager实例。 |
| [AudioSessionDeactivatedEvent](arkts-audio-audio-audiosessiondeactivatedevent-i.md) | 音频会话停用事件。 |
| [AudioSessionManager](arkts-audio-audio-audiosessionmanager-i.md) | 音频会话管理。 在使用AudioSessionManager的接口之前，需先通过 [getSessionManager](arkts-audio-audio-audiomanager-i.md#getsessionmanager)获取AudioSessionManager实例。 |
| [AudioSessionStateChangedEvent](arkts-audio-audio-audiosessionstatechangedevent-i.md) | 音频会话状态变更事件。 |
| [AudioSessionStrategy](arkts-audio-audio-audiosessionstrategy-i.md) | 音频会话策略。@ |
| [AudioSpatializationManager](arkts-audio-audio-audiospatializationmanager-i.md) | 空间音频管理。在使用AudioSpatializationManager的接口前，需要使用 [getSpatializationManager](arkts-audio-audio-audiomanager-i.md#getspatializationmanager)获取 AudioSpatializationManager实例。 |
| [AudioStreamDeviceChangeInfo](arkts-audio-audio-audiostreamdevicechangeinfo-i.md) | 流设备变更时，应用接收到的事件。 |
| [AudioStreamInfo](arkts-audio-audio-audiostreaminfo-i.md) | 音频流信息。 |
| [AudioStreamManager](arkts-audio-audio-audiostreammanager-i.md) | 音频流管理。 在使用AudioStreamManager的接口之前，需先通过[getStreamManager](arkts-audio-audio-audiomanager-i.md#getstreammanager) 获取AudioStreamManager实例。 |
| [AudioTimestampInfo](arkts-audio-audio-audiotimestampinfo-i.md) | 音频流时间戳和当前数据帧位置信息。 |
| [AudioVolumeGroupManager](arkts-audio-audio-audiovolumegroupmanager-i.md) | 管理音频组音量。在调用AudioVolumeGroupManager的接口前，需要先通过 [getVolumeGroupManager](arkts-audio-audio-audiovolumemanager-i.md#getvolumegroupmanager) 创建实例。 |
| [AudioVolumeManager](arkts-audio-audio-audiovolumemanager-i.md) | 音量管理。在使用AudioVolumeManager的接口前，需要使用 [getVolumeManager](arkts-audio-audio-audiomanager-i.md#getvolumemanager)获取AudioVolumeManager实例。 |
| [CaptureFilterOptions](arkts-audio-audio-capturefilteroptions-i.md) | 待录制的播放音频流的筛选信息。 |
| [CurrentInputDeviceChangedEvent](arkts-audio-audio-currentinputdevicechangedevent-i.md) | 应用接收到输入设备的变更事件。 |
| [CurrentOutputDeviceChangedEvent](arkts-audio-audio-currentoutputdevicechangedevent-i.md) | 应用接收到输出设备的变更事件。 |
| [DeviceBlockStatusInfo](arkts-audio-audio-deviceblockstatusinfo-i.md) | 描述音频设备被堵塞状态和设备信息。 |
| [DeviceChangeAction](arkts-audio-audio-devicechangeaction-i.md) | 描述设备连接状态变化和设备信息。 |
| [InterruptAction](arkts-audio-audio-interruptaction-i.md) | 音频打断/获取焦点事件的回调方法。 |
| [InterruptEvent](arkts-audio-audio-interruptevent-i.md) | 音频中断时，应用接收的中断事件。 |
| [MicStateChangeEvent](arkts-audio-audio-micstatechangeevent-i.md) | 麦克风状态变化时，应用接收到的事件。 |
| [StreamVolumeEvent](arkts-audio-audio-streamvolumeevent-i.md) | 音频流音量变化时，应用接收到的事件。 |
| [SystemRecordControllerConfig](arkts-audio-audio-systemrecordcontrollerconfig-i.md) | 系统录音控制面板的配置信息。 |
| [VolumeEvent](arkts-audio-audio-volumeevent-i.md) | 音量改变时，应用接收的事件。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ActiveStreamVolumeInfo](arkts-audio-audio-activestreamvolumeinfo-i-sys.md) | 活动音频流的音量信息。 |
| [AppIdInfo](arkts-audio-audio-appidinfo-i-sys.md) | 应用ID信息，包含应用的UID（标识应用身份）、PID（标识运行中的进程）、Token ID（用于常规身份识别与权限校验）和FullToken ID（携带应用完整身份权限信息，用于原始应用溯源与全链路权限校验）。 |
| [AsrProcessingController](arkts-audio-audio-asrprocessingcontroller-i-sys.md) | 自动语音识别（ASR）处理控制器。 |
| [AudioCapturer](arkts-audio-audio-audiocapturer-i-sys.md) | 提供音频采集的相关接口。在使用AudioCapturer的接口之前，需先通过 [createAudioCapturer](arkts-audio-audio-createaudiocapturer-f.md) 获取AudioCapturer实例。 |
| [AudioCapturerChangeInfo](arkts-audio-audio-audiocapturerchangeinfo-i-sys.md) | 描述音频采集器更改信息。 |
| [AudioCapturerFilter](arkts-audio-audio-audiocapturerfilter-i-sys.md) | 过滤条件类。在调用selectOutputDeviceByFilter接口前，需要先创建AudioCapturerFilter实例。 |
| [AudioCapturerMicInConfig](arkts-audio-audio-audiocapturermicinconfig-i-sys.md) | 音频采集器选项信息，可采集未经任何处理的麦克风输入（mic-in）音频数据。 |
| [AudioCapturerMicInData](arkts-audio-audio-audiocapturermicindata-i-sys.md) | 音频采集器数据，包含处理后的音频数据和未经任何处理的麦克风输入（mic-in）音频数据。 |
| [AudioCapturerOptions](arkts-audio-audio-audiocaptureroptions-i-sys.md) | 音频采集器选项信息。 |
| [AudioCollaborativeManager](arkts-audio-audio-audiocollaborativemanager-i-sys.md) | 移动全景声管理器。 在使用AudioCollaborativeManager的接口前，需要先使用[getCollaborativeManager](arkts-audio-audio-audiomanager-i-sys.md#getcollaborativemanager)获取 AudioCollaborativeManager实例。 |
| [AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i-sys.md) | 描述音频设备。 |
| [AudioDeviceEnhanceManager](arkts-audio-audio-audiodeviceenhancemanager-i-sys.md) | 音频设备增强管理功能，用于应用级音频设备选择及流维度音频设备选择。 在使用AudioDeviceEnhanceManager的接口之前，需要先通过getDeviceEnhanceManager获取AudioDeviceEnhanceManager实例。 |
| [AudioEffectManager](arkts-audio-audio-audioeffectmanager-i-sys.md) | 音频效果管理。在使用AudioEffectManager的接口前，需要使用[getEffectManager](arkts-audio-audio-audiomanager-i-sys.md#geteffectmanager)获取 AudioEffectManager实例。 |
| [AudioEffectProperty](arkts-audio-audio-audioeffectproperty-i-sys.md) | 音效属性。 |
| [AudioHRTFAnonymousDescriptor](arkts-audio-audio-audiohrtfanonymousdescriptor-i-sys.md) | 用于跨进程传输的匿名个性化HRTF文件描述符。 |
| [AudioManager](arkts-audio-audio-audiomanager-i-sys.md) | 管理音频音量和音频设备。在调用AudioManager的接口前，需要先通过[getAudioManager](arkts-audio-audio-getaudiomanager-f.md)创建实例。 |
| [AudioPersonalizedSpatialEnabledChangeForAnyDevice](arkts-audio-audio-audiopersonalizedspatialenabledchangeforanydevice-i-sys.md) | 此接口用于通知监听器任何设备个性化空间化启用状态的变化。 |
| [AudioRecordingManager](arkts-audio-audio-audiorecordingmanager-i-sys.md) | 录音策略管理，提供协同录音和录音控制能力。 在使用AudioRecordingManager的接口之前，需先通过 getRecordingManager获取AudioRecordingManager实例 。 |
| [AudioRenderer](arkts-audio-audio-audiorenderer-i-sys.md) | 音频渲染。在使用AudioRenderer的接口之前，需先通过 [audio.createAudioRenderer](arkts-audio-audio-createaudiorenderer-f.md) 获取AudioRenderer实例。 |
| [AudioRendererChangeInfo](arkts-audio-audio-audiorendererchangeinfo-i-sys.md) | 描述音频渲染器更改信息。 |
| [AudioRendererFilter](arkts-audio-audio-audiorendererfilter-i-sys.md) | 音频渲染器过滤条件。 |
| [AudioRendererOptions](arkts-audio-audio-audiorendereroptions-i-sys.md) | 音频渲染器选项信息。 |
| [AudioRoutingManager](arkts-audio-audio-audioroutingmanager-i-sys.md) | 音频路由管理。在使用AudioRoutingManager的接口前，需要使用 [getRoutingManager](arkts-audio-audio-audiomanager-i.md#getroutingmanager)获取AudioRoutingManager实例。 |
| [AudioSpatialDeviceState](arkts-audio-audio-audiospatialdevicestate-i-sys.md) | 空间化设备状态。 |
| [AudioSpatialEnabledStateForDevice](arkts-audio-audio-audiospatialenabledstatefordevice-i-sys.md) | 监听设备空间音频开关状态。@interface AudioSpatialEnabledStateForDevice |
| [AudioSpatializationManager](arkts-audio-audio-audiospatializationmanager-i-sys.md) | 空间音频管理。在使用AudioSpatializationManager的接口前，需要使用 [getSpatializationManager](arkts-audio-audio-audiomanager-i.md#getspatializationmanager)获取 AudioSpatializationManager实例。 |
| [AudioVolumeGroupManager](arkts-audio-audio-audiovolumegroupmanager-i-sys.md) | 管理音频组音量。在调用AudioVolumeGroupManager的接口前，需要先通过 [getVolumeGroupManager](arkts-audio-audio-audiovolumemanager-i.md#getvolumegroupmanager) 创建实例。 |
| [AudioVolumeManager](arkts-audio-audio-audiovolumemanager-i-sys.md) | 音量管理。在使用AudioVolumeManager的接口前，需要使用 [getVolumeManager](arkts-audio-audio-audiomanager-i.md#getvolumemanager)获取AudioVolumeManager实例。 |
| [CollaborativeRecordingConfiguration](arkts-audio-audio-collaborativerecordingconfiguration-i-sys.md) | 描述协作录制的配置。 |
| [InterruptResult](arkts-audio-audio-interruptresult-i-sys.md) | 音频中断结果。 |
| [NoiseReductionCapability](arkts-audio-audio-noisereductioncapability-i-sys.md) | 支持降噪能力的外部音频设备信息。 |
| [NoiseReductionConfigAction](arkts-audio-audio-noisereductionconfigaction-i-sys.md) | 降噪配置操作。 |
| [SoundCardInfo](arkts-audio-audio-soundcardinfo-i-sys.md) | 描述声卡信息。 |
| [SystemRecordControllerChangeInfo](arkts-audio-audio-systemrecordcontrollerchangeinfo-i-sys.md) | 定义系统记录控制器状态变化时所携带的信息。 它包括启用状态、应用程序UID和预期的音频源类型。 |
| [SystemVolumeFilter](arkts-audio-audio-systemvolumefilter-i-sys.md) | 描述系统音量过滤器。 |
| [TonePlayer](arkts-audio-audio-toneplayer-i-sys.md) | 提供播放和管理DTMF（Dual Tone Multi Frequency，双音多频）音调的方法，包括各种系统监听音调、专有音调，如拨号音、通话回铃音等。 在调用TonePlayer的接口前，需要先通过 [createTonePlayer](arkts-audio-audio-createtoneplayer-f-sys.md)创建 实例。 |
| [VolumeEvent](arkts-audio-audio-volumeevent-i-sys.md) | 音量改变时，应用接收的事件。 |
| [VolumeGroupInfo](arkts-audio-audio-volumegroupinfo-i-sys.md) | 音量组信息。 |
| [VolumeLimitExceededEvent](arkts-audio-audio-volumelimitexceededevent-i-sys.md) | 描述表示音量超过阈值的通知事件。 在收到通知后，应用必须发送确认结果。 在继续调整音量之前，通过 [confirmVolumeLimitExceeded](arkts-audio-audio-audiovolumemanager-i-sys.md#confirmvolumelimitexceeded) 进行确认。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [ActiveDeviceType](arkts-audio-audio-activedevicetype-e.md) | 表示活跃设备类型的枚举。 |
| [AudioChannel](arkts-audio-audio-audiochannel-e.md) | 表示音频声道的枚举。 |
| [AudioChannelLayout](arkts-audio-audio-audiochannellayout-e.md) | 表示音频文件声道布局类型的枚举。 |
| [AudioConcurrencyMode](arkts-audio-audio-audioconcurrencymode-e.md) | 表示音频并发模式的枚举。 |
| [AudioDataCallbackResult](arkts-audio-audio-audiodatacallbackresult-e.md) | 表示音频数据回调结果的枚举。@enum { number } |
| [AudioEffectMode](arkts-audio-audio-audioeffectmode-e.md) | 表示音效模式的枚举。 |
| [AudioEncodingType](arkts-audio-audio-audioencodingtype-e.md) | 表示音频编码类型的枚举。 |
| [AudioErrors](arkts-audio-audio-audioerrors-e.md) | 表示音频错误码的枚举。 |
| [AudioLatencyType](arkts-audio-audio-audiolatencytype-e.md) | 表示音频时延类型的枚举。 |
| [AudioLoopbackEqualizerPreset](arkts-audio-audio-audioloopbackequalizerpreset-e.md) | 表示返听均衡器类型的枚举。@enum { number } |
| [AudioLoopbackMode](arkts-audio-audio-audioloopbackmode-e.md) | 表示返听模式的枚举。 |
| [AudioLoopbackReverbPreset](arkts-audio-audio-audioloopbackreverbpreset-e.md) | 表示返听混响模式的枚举。@enum { number } |
| [AudioLoopbackStatus](arkts-audio-audio-audioloopbackstatus-e.md) | 表示返听状态的枚举。@enum { number } |
| [AudioPlaybackCaptureMode](arkts-audio-audio-audioplaybackcapturemode-e.md) | 表示内录（录制设备内部应用的声音）模式的枚举。不同模式决定可录制的目标播放流类型。支持通过按位或组合枚举值，当前仅支持MODE_DEFAULT（0x0）、MODE_MEDIA（0x1）、MODE_EXCLUDING_SELF（0x 8000），以及MODE_MEDIA和MODE_EXCLUDING_SELF的按位或组合（0x8001）。 |
| [AudioPrivacyType](arkts-audio-audio-audioprivacytype-e.md) | 表示对应播放音频流是否支持被其他应用录制的枚举。 |
| [AudioRendererRate](arkts-audio-audio-audiorendererrate-e.md) | 表示音频渲染速度的枚举。 |
| [AudioRingMode](arkts-audio-audio-audioringmode-e.md) | 表示铃声模式的枚举。 |
| [AudioSampleFormat](arkts-audio-audio-audiosampleformat-e.md) | 表示音频采样格式的枚举。 |
| [AudioSamplingRate](arkts-audio-audio-audiosamplingrate-e.md) | 表示音频采样率的枚举（具体设备支持的采样率规格会存在差异）。 |
| [AudioScene](arkts-audio-audio-audioscene-e.md) | 表示音频场景的枚举。 |
| [AudioSessionBehaviorFlags](arkts-audio-audio-audiosessionbehaviorflags-e.md) | 表示音频会话行为的枚举。 |
| [AudioSessionDeactivatedReason](arkts-audio-audio-audiosessiondeactivatedreason-e.md) | 表示音频会话停用原因的枚举。 |
| [AudioSessionScene](arkts-audio-audio-audiosessionscene-e.md) | 枚举音频会话场景。 |
| [AudioSessionStateChangeHint](arkts-audio-audio-audiosessionstatechangehint-e.md) | 枚举用于音频会话状态变更提示。 当用户监听到音频会话状态变化事件（即收到 [AudioSessionStateChangedEvent](arkts-audio-audio-audiosessionstatechangedevent-i.md)事件）时，获取相关信息。 此类型表示根据焦点策略对音频会话执行的操作，包括暂停、调整音量等。 详情请参阅音频会话管理文档。 |
| [AudioState](arkts-audio-audio-audiostate-e.md) | 表示音频状态的枚举。 |
| [AudioStreamDeviceChangeReason](arkts-audio-audio-audiostreamdevicechangereason-e.md) | 表示流设备变更原因的枚举。 |
| [AudioVolumeMode](arkts-audio-audio-audiovolumemode-e.md) | 表示音量模式的枚举。@enum { number } |
| [AudioVolumeType](arkts-audio-audio-audiovolumetype-e.md) | 枚举，音频流类型。 |
| [BluetoothAndNearlinkPreferredRecordCategory](arkts-audio-audio-bluetoothandnearlinkpreferredrecordcategory-e.md) | 表示在使用蓝牙或星闪进行录音时，应用程序的设备偏好分类枚举。 |
| [ChannelBlendMode](arkts-audio-audio-channelblendmode-e.md) | 表示声道混合模式类型的枚举。 |
| [CommunicationDeviceType](arkts-audio-audio-communicationdevicetype-e.md) | 表示用于通信的可用设备类型的枚举。@enum { number } |
| [ContentType](arkts-audio-audio-contenttype-e.md) | 表示音频内容类型的枚举。 |
| [DeviceBlockStatus](arkts-audio-audio-deviceblockstatus-e.md) | 表示音频设备是否被堵塞的枚举。 |
| [DeviceChangeType](arkts-audio-audio-devicechangetype-e.md) | 表示设备连接状态变化的枚举。 |
| [DeviceFlag](arkts-audio-audio-deviceflag-e.md) | 枚举，可获取的设备种类。 |
| [DeviceRole](arkts-audio-audio-devicerole-e.md) | 表示设备角色的枚举。 |
| [DeviceType](arkts-audio-audio-devicetype-e.md) | 表示设备类型的枚举。 |
| [DeviceUsage](arkts-audio-audio-deviceusage-e.md) | 表示音频设备类型的枚举（根据用途分类）。@enum { number } |
| [InterruptActionType](arkts-audio-audio-interruptactiontype-e.md) | 表示中断事件返回类型的枚举。 |
| [InterruptForceType](arkts-audio-audio-interruptforcetype-e.md) | 表示音频打断类型的枚举。 当用户监听到音频中断（即收到[InterruptEvent](arkts-audio-audio-interruptevent-i.md)事件）时，获取此信息。 此类型表示音频打断是否已由系统强制执行，具体操作信息（如音频暂停、停止等）可通过[InterruptHint](arkts-audio-audio-interrupthint-e.md)获取。 关于音频打断策略的详细说明可参考音频焦点介绍文档。 |
| [InterruptHint](arkts-audio-audio-interrupthint-e.md) | 表示中断提示的枚举。 当用户监听到音频中断事件（即收到[InterruptEvent](arkts-audio-audio-interruptevent-i.md)事件）时，获取此信息。 此类型表示根据焦点策略，对音频流执行的具体操作（如暂停、调整音量等）。 可以结合InterruptEvent中的[InterruptForceType](arkts-audio-audio-interruptforcetype-e.md)信息，判断该操作是否已由系统强制执行。详情请参阅音频焦点介绍文档。 |
| [InterruptMode](arkts-audio-audio-interruptmode-e.md) | 表示焦点模型的枚举。 |
| [InterruptType](arkts-audio-audio-interrupttype-e.md) | 表示中断类型的枚举。 |
| [NoiseReductionMode](arkts-audio-audio-noisereductionmode-e.md) | 表示录音降噪模式的枚举。 |
| [OutputDeviceChangeRecommendedAction](arkts-audio-audio-outputdevicechangerecommendedaction-e.md) | 表示输出设备变更后推荐操作的枚举。 常见场景示例：耳机设备和外放设备之间进行切换。当佩戴耳机时，从外放设备切换到耳机设备，系统会推荐继续播放，提示应用无需停止当前播放。当摘下耳机设备切换到外放设备时，系统会推荐停止播放。 |
| [PlaybackCaptureStartState](arkts-audio-audio-playbackcapturestartstate-e.md) | 表示调用[requestPlaybackCaptureStart](arkts-audio-audio-audiocapturer-i.md#requestplaybackcapturestart)后异步返 回的内录启动状态的枚举。 |
| [SourceType](arkts-audio-audio-sourcetype-e.md) | 枚举，音源类型。 |
| [StreamUsage](arkts-audio-audio-streamusage-e.md) | 枚举，音频流使用类型。 |

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AsrAecMode](arkts-audio-audio-asraecmode-e-sys.md) | 枚举，自动语音识别（ASR）的声学回声消除（AEC）模式。@enum { number } |
| [AsrNoiseSuppressionMode](arkts-audio-audio-asrnoisesuppressionmode-e-sys.md) | 枚举，自动语音识别（ASR）的噪音抑制模式。@enum { number } |
| [AsrVoiceControlMode](arkts-audio-audio-asrvoicecontrolmode-e-sys.md) | 枚举，自动语音识别（ASR）的音频通路模式。 |
| [AsrVoiceMuteMode](arkts-audio-audio-asrvoicemutemode-e-sys.md) | 枚举，自动语音识别（ASR）的静音模式。 |
| [AsrWhisperDetectionMode](arkts-audio-audio-asrwhisperdetectionmode-e-sys.md) | 枚举，自动语音识别（ASR）的耳语检测模式。 |
| [AudioDevcieSelectStrategy](arkts-audio-audio-audiodevcieselectstrategy-e-sys.md) | 表示设备选择策略的枚举。 |
| [AudioSeparationVolumeType](arkts-audio-audio-audioseparationvolumetype-e-sys.md) | 表示音频分离效果的音量类型。 |
| [AudioSpatialDeviceType](arkts-audio-audio-audiospatialdevicetype-e-sys.md) | 枚举，空间化设备类型。 |
| [AudioSpatializationSceneType](arkts-audio-audio-audiospatializationscenetype-e-sys.md) | 枚举，空间音频渲染场景类型。 |
| [AudioVolumeType](arkts-audio-audio-audiovolumetype-e-sys.md) | 枚举，音频流类型。 |
| [ConnectType](arkts-audio-audio-connecttype-e-sys.md) | 枚举，设备连接类型。@enum { number } |
| [DeviceFlag](arkts-audio-audio-deviceflag-e-sys.md) | 枚举，可获取的设备种类。 |
| [DeviceType](arkts-audio-audio-devicetype-e-sys.md) | 表示设备类型的枚举。 |
| [EffectFlag](arkts-audio-audio-effectflag-e-sys.md) | 枚举，音效分类。@enum { number } |
| [InterruptRequestResultType](arkts-audio-audio-interruptrequestresulttype-e-sys.md) | 枚举，音频中断请求结果类型。 |
| [InterruptRequestType](arkts-audio-audio-interruptrequesttype-e-sys.md) | 枚举，音频中断请求类型。 |
| [PolicyType](arkts-audio-audio-policytype-e-sys.md) | 表示静音策略类型的枚举。@enum { number } |
| [RenderTarget](arkts-audio-audio-rendertarget-e-sys.md) | 枚举，音频渲染器的渲染目标。@enum { number } |
| [SourceType](arkts-audio-audio-sourcetype-e-sys.md) | 枚举，音源类型。 |
| [SpatialAudioSourceType](arkts-audio-audio-spatialaudiosourcetype-e-sys.md) | 枚举空间音频源类型。 |
| [StreamUsage](arkts-audio-audio-streamusage-e-sys.md) | 枚举，音频流使用类型。 |
| [ToneType](arkts-audio-audio-tonetype-e-sys.md) | 枚举，播放器的音调类型。 |
| [VolumeAdjustType](arkts-audio-audio-volumeadjusttype-e-sys.md) | 枚举，音量调节类型。 |
| [VolumeFlag](arkts-audio-audio-volumeflag-e-sys.md) | 枚举，音量相关操作。 |
<!--DelEnd-->

### 类型

| 名称 | 说明 |
| --- | --- |
| [AudioCapturerChangeInfoArray](arkts-audio-audio-audiocapturerchangeinfoarray-t.md) | 数组类型，AudioCapturerChangeInfo数组，只读。 |
| [AudioDeviceDescriptors](arkts-audio-audio-audiodevicedescriptors-t.md) | 设备属性数组类型，为[AudioDeviceDescriptor](arkts-audio-audio-audiodevicedescriptor-i.md)的数组，只读。 |
| [AudioEffectInfoArray](arkts-audio-audio-audioeffectinfoarray-t.md) | 待查询ContentType和StreamUsage组合场景下的音效模式数组类型，[AudioEffectMode](arkts-audio-audio-audioeffectmode-e.md)数组，只读 。 |
| [AudioRendererChangeInfoArray](arkts-audio-audio-audiorendererchangeinfoarray-t.md) | 数组类型，AudioRendererChangeInfo数组，只读。 |
| [AudioRendererWriteDataCallback](arkts-audio-audio-audiorendererwritedatacallback-t.md) | 回调函数类型，用于音频渲染器的数据写入，回调函数结束后，音频服务会把data指向的数据放入队列里等待播放，因此请勿在回调外再次更改data指向的数据, 且务必保证往data填满待播放数据, 否则会导致音频服务播放杂音。 |
| [DeviceTypeArray](arkts-audio-audio-devicetypearray-t.md) | 数组类型，[DeviceType](arkts-audio-audio-devicetype-e.md)数组。 |

<!--Del-->
### 类型（系统接口）

| 名称 | 说明 |
| --- | --- |
| [ActiveStreamsVolumeInfoArray](arkts-audio-audio-activestreamsvolumeinfoarray-t-sys.md) | ActiveStreamVolumeInfo数组。 |
| [StreamUsageArray](arkts-audio-audio-streamusagearray-t-sys.md) | 音频类型数组 |
| [VolumeGroupInfos](arkts-audio-audio-volumegroupinfos-t-sys.md) |  |
<!--DelEnd-->

### 常量

| 名称 | 说明 |
| --- | --- |
| DEFAULT_INTERRUPT_GROUP_ID | 默认焦点组ID。 |
| DEFAULT_VOLUME_GROUP_ID | 默认音量组ID。 |

<!--Del-->
### 常量（系统接口）

| 名称 | 说明 |
| --- | --- |
| [LOCAL_NETWORK_ID](arkts-audio-audio-con-sys.md#local_network_id) | 本地设备网络id。 |
<!--DelEnd-->
