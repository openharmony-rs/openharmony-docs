# Interfaces (其他)
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

> **说明：**
>
> 本模块首批接口从API version 7开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。

## AudioStreamInfo<sup>8+</sup>

音频流信息。

**系统能力：** SystemCapability.Multimedia.Audio.Core

| 名称         | 类型                                               | 只读 | 可选 | 说明               |
| ------------ | ------------------------------------------------- | ---- |---| ------------------ |
| samplingRate | [AudioSamplingRate](arkts-apis-audio-e.md#audiosamplingrate8)          | 否 | 否 | 音频文件的采样率。 |
| channels     | [AudioChannel](arkts-apis-audio-e.md#audiochannel8)                    | 否 | 否 | 音频文件的通道数。 |
| sampleFormat | [AudioSampleFormat](arkts-apis-audio-e.md#audiosampleformat8)          | 否 | 否 | 音频采样格式。     |
| encodingType | [AudioEncodingType](arkts-apis-audio-e.md#audioencodingtype8)          | 否 | 否 | 音频编码格式。     |
| channelLayout<sup>11+</sup> | [AudioChannelLayout](arkts-apis-audio-e.md#audiochannellayout11)  | 否 | 是 | 音频声道布局，默认值为0x0。 |

## AudioRendererInfo<sup>8+</sup>

音频渲染器信息。

| 名称          | 类型                        | 只读 | 可选 | 说明            |
| ------------- | --------------------------- | ---- |---| --------------- |
| content       | [ContentType](arkts-apis-audio-e.md#contenttypedeprecated) | 否 | 是 | 音频内容类型。<br/>**系统能力：** SystemCapability.Multimedia.Audio.Core <br>API version 8、9为必填参数，从API version 10开始为可选参数，默认值为CONTENT_TYPE_UNKNOWN。<br>从API version 7开始支持，从API version 10开始废弃，建议使用[StreamUsage](arkts-apis-audio-e.md#streamusage)替代。 |
| usage         | [StreamUsage](arkts-apis-audio-e.md#streamusage) | 否 | 否 | 音频流使用类型。<br/>**系统能力：** SystemCapability.Multimedia.Audio.Core <br/>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。|
| rendererFlags | number                      | 否 | 否 | 音频渲染器标志。<br>0代表音频渲染器。<br/>**系统能力：** SystemCapability.Multimedia.Audio.Core <br/>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。|
| volumeMode<sup>19+</sup> | [AudioVolumeMode](arkts-apis-audio-e.md#audiovolumemode19) | 否 | 是 | 音频的音量模式。默认值为SYSTEM_GLOBAL。<br/>**系统能力：** SystemCapability.Multimedia.Audio.Volume|

## AudioRendererOptions<sup>8+</sup>

音频渲染器选项信息。

| 名称         | 类型                                     | 只读 | 可选 | 说明             |
| ------------ | ---------------------------------------- | ---- |---| ---------------- |
| streamInfo   | [AudioStreamInfo](#audiostreaminfo8)     | 否 | 否 | 音频流信息。<br/>**系统能力：** SystemCapability.Multimedia.Audio.Renderer |
| rendererInfo | [AudioRendererInfo](#audiorendererinfo8) | 否 | 否 | 音频渲染器信息。<br/>**系统能力：** SystemCapability.Multimedia.Audio.Renderer |
| privacyType<sup>10+</sup> | [AudioPrivacyType](arkts-apis-audio-e.md#audioprivacytype10) | 否 | 是 | 表示音频流是否可以被其他应用录制，默认值为0。<br/>**系统能力：** SystemCapability.Multimedia.Audio.PlaybackCapture |

## InterruptEvent<sup>9+</sup>

音频中断时，应用接收的中断事件。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

| 名称      | 类型                                       | 只读 | 可选 | 说明                                 |
| --------- | ------------------------------------------ | ---- |---| ------------------------------------ |
| eventType | [InterruptType](arkts-apis-audio-e.md#interrupttype)            | 否 | 否 | 音频中断事件类型，开始或是结束。         |
| forceType | [InterruptForceType](arkts-apis-audio-e.md#interruptforcetype9) | 否 | 否 | 操作是由系统强制执行或是由应用程序执行。 |
| hintType  | [InterruptHint](arkts-apis-audio-e.md#interrupthint)            | 否 | 否 | 中断提示，用于提供中断事件的相关信息。 |

## DeviceBlockStatusInfo<sup>13+</sup>

描述音频设备被堵塞状态和设备信息。

**系统能力：** SystemCapability.Multimedia.Audio.Device

| 名称              | 类型                                              | 只读 | 可选 | 说明               |
| :---------------- | :------------------------------------------------ | :--- |---| :----------------- |
| blockStatus       | [DeviceBlockStatus](arkts-apis-audio-e.md#deviceblockstatus13)           | 否 | 否 | 音频设备堵塞状态。 |
| devices | [AudioDeviceDescriptors](arkts-apis-audio-t.md#audiodevicedescriptors) | 否 | 否 | 设备信息。         |

## AudioSessionStrategy<sup>12+</sup>

音频会话策略。

**系统能力：** SystemCapability.Multimedia.Audio.Core

| 名称          | 类型                                              | 只读 | 可选 | 说明             |
| :------------ |:------------------------------------------------| :--- |---| :--------------- |
| concurrencyMode        | [AudioConcurrencyMode](arkts-apis-audio-e.md#audioconcurrencymode12) | 否 | 否 | 音频并发模式。       |

## AudioSessionDeactivatedEvent<sup>12+</sup>

音频会话停用事件。

**系统能力：** SystemCapability.Multimedia.Audio.Core

| 名称          | 类型                                                                | 只读 | 可选 | 说明             |
| :------------ |:------------------------------------------------------------------| :--- |---| :--------------- |
| reason        | [AudioSessionDeactivatedReason](arkts-apis-audio-e.md#audiosessiondeactivatedreason12) | 否 | 否 | 音频会话停用原因。       |

## AudioSessionStateChangedEvent<sup>20+</sup>

音频会话状态变更事件。

**系统能力：** SystemCapability.Multimedia.Audio.Core

| 名称          | 类型                                              | 只读 | 可选 | 说明             |
| :------------ |:------------------------------------------------| :--- |---| :--------------- |
| stateChangeHint        | [AudioSessionStateChangeHint](arkts-apis-audio-e.md#audiosessionstatechangehint20) | 否 | 否 | 音频会话状态变更提示。 |

## AudioRendererChangeInfo<sup>9+</sup>

描述音频渲染器更改信息。

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

| 名称               | 类型                                       | 只读 | 可选 | 说明                          |
| -------------------| ----------------------------------------- | ---- | ---- | ---------------------------- |
| streamId           | number                                    | 是   | 否   | 音频流唯一id。                |
| rendererInfo       | [AudioRendererInfo](#audiorendererinfo8)  | 是   | 否   | 音频渲染器信息。               |
| deviceDescriptors  | [AudioDeviceDescriptors](arkts-apis-audio-t.md#audiodevicedescriptors)      | 是   | 否   | 音频设备描述。|

## AudioCapturerChangeInfo<sup>9+</sup>

描述音频采集器更改信息。

**系统能力：** SystemCapability.Multimedia.Audio.Capturer

| 名称               | 类型                                       | 只读 | 可选 | 说明                          |
| -------------------| ----------------------------------------- | ---- | ---- | ---------------------------- |
| streamId           | number                                    | 是   | 否   | 音频流唯一id。                |
| capturerInfo       | [AudioCapturerInfo](#audiocapturerinfo8)  | 是   | 否   | 音频采集器信息。               |
| deviceDescriptors  | [AudioDeviceDescriptors](arkts-apis-audio-t.md#audiodevicedescriptors)      | 是   | 否   | 音频设备信息。|
| muted<sup>11+</sup>  | boolean    | 是   | 是 | 音频采集器是否处于静音状态。true表示静音，false表示非静音。|

## AudioDeviceDescriptor

描述音频设备。

| 名称                          | 类型                       | 只读 | 可选 | 说明       |
| ----------------------------- | -------------------------- | ---- | ---- | ---------- |
| deviceRole                    | [DeviceRole](arkts-apis-audio-e.md#devicerole)  | 是   | 否   | 设备角色。 <br> **系统能力：** SystemCapability.Multimedia.Audio.Device <br/>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。|
| deviceType                    | [DeviceType](arkts-apis-audio-e.md#devicetype)  | 是   | 否   | 设备类型。 <br> **系统能力：** SystemCapability.Multimedia.Audio.Device <br/>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。|
| id<sup>9+</sup>               | number                     | 是   | 否   | 唯一的设备id。  <br> **系统能力：** SystemCapability.Multimedia.Audio.Device <br/>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。|
| name<sup>9+</sup>             | string                     | 是   | 否   | 设备名称。<br>如果是蓝牙设备，需要申请权限ohos.permission.USE_BLUETOOTH。 <br> **系统能力：** SystemCapability.Multimedia.Audio.Device <br/>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。|
| address<sup>9+</sup>          | string                     | 是   | 否   | 设备地址。<br>如果是蓝牙设备，需要申请权限ohos.permission.USE_BLUETOOTH。 <br> **系统能力：** SystemCapability.Multimedia.Audio.Device <br/>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。|
| sampleRates<sup>9+</sup>      | Array&lt;number&gt;        | 是   | 否   | 支持的采样率。 <br> **系统能力：** SystemCapability.Multimedia.Audio.Device <br/>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。|
| channelCounts<sup>9+</sup>    | Array&lt;number&gt;        | 是   | 否   | 支持的通道数。 <br> **系统能力：** SystemCapability.Multimedia.Audio.Device <br/>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。|
| channelMasks<sup>9+</sup>     | Array&lt;number&gt;        | 是   | 否   | 支持的通道掩码。 <br> **系统能力：** SystemCapability.Multimedia.Audio.Device <br/>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。|
| displayName<sup>10+</sup>     | string                     | 是   | 否   | 设备显示名。 <br> **系统能力：** SystemCapability.Multimedia.Audio.Device <br/>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。|
| encodingTypes<sup>11+</sup>    | Array&lt;[AudioEncodingType](arkts-apis-audio-e.md#audioencodingtype8)&gt;                     | 是   | 是 | 支持的编码类型。 <br> **系统能力：** SystemCapability.Multimedia.Audio.Core <br/>**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。|
| spatializationSupported<sup>18+</sup>     | boolean                     | 是   | 是 | 设备是否支持空间音频。true表示支持空间音频，false表示不支持空间音频。 <br> **系统能力：** SystemCapability.Multimedia.Audio.Spatialization|

## VolumeEvent<sup>9+</sup>

音量改变时，应用接收到的事件。

**系统能力：** SystemCapability.Multimedia.Audio.Volume

| 名称       | 类型                                | 只读 | 可选 | 说明                                        |
| ---------- | ----------------------------------- | ---- |---|-------------------------------------------|
| volumeType | [AudioVolumeType](arkts-apis-audio-e.md#audiovolumetype) | 否 | 否 | 音量流类型。                                    |
| volume     | number                              | 否 | 否 |音量等级，可设置范围通过调用getMinVolume和getMaxVolume方法获取。  |
| updateUi   | boolean                             | 否 | 否 |  是否在UI中显示音量变化。true表示显示，false表示不显示。             |
| volumeMode<sup>19+</sup> | [AudioVolumeMode](arkts-apis-audio-e.md#audiovolumemode19) | 否 | 是 | 音频的音量模式。默认值为SYSTEM_GLOBAL。|


## MicStateChangeEvent<sup>9+</sup>

麦克风状态变化时，应用接收到的事件。

**系统能力：** SystemCapability.Multimedia.Audio.Device

| 名称       | 类型                                | 只读 | 可选 | 说明                                                     |
| ---------- | ----------------------------------- | ---- |---|-------------------------------------------------------- |
| mute | boolean | 否 | 否 | 系统麦克风是否为静音状态。true表示静音，false表示非静音。          |


## StreamVolumeEvent<sup>20+</sup>

音频流音量变化时，应用接收到的事件。

**系统能力：** SystemCapability.Multimedia.Audio.Volume

| 名称       | 类型                                | 只读 | 可选 | 说明                                                     |
| ---------- | ----------------------------------- | ---- |---|-------------------------------------------------------- |
| streamUsage | [StreamUsage](arkts-apis-audio-e.md#streamusage) | 否 | 否 | 音量发生变化的音频流。          |
| volume | number | 否 | 否 | 音量值。          |
| updateUi | boolean | 否 | 否 | 是否在UI上展示音量变化。true表示展示，false表示不展示。          |

## DeviceChangeAction

描述设备连接状态变化和设备信息。

**系统能力：** SystemCapability.Multimedia.Audio.Device

| 名称              | 类型                                              | 只读 | 可选 | 说明               |
| :---------------- | :------------------------------------------------ | :--- |---| :----------------- |
| type              | [DeviceChangeType](arkts-apis-audio-e.md#devicechangetype)             | 否 | 否 | 设备连接状态变化。 |
| deviceDescriptors | [AudioDeviceDescriptors](arkts-apis-audio-t.md#audiodevicedescriptors) | 否 | 否 | 设备信息。         |

## AudioStreamDeviceChangeInfo<sup>11+</sup>

流设备变更时，应用接收到的事件。

**原子化服务API：** 从API version 12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Multimedia.Audio.Device

| 名称              | 类型                                                                | 只读 | 可选 | 说明               |
| :---------------- |:------------------------------------------------------------------| :--- |---| :----------------- |
| devices              | [AudioDeviceDescriptors](arkts-apis-audio-t.md#audiodevicedescriptors)                 | 否 | 否 | 设备信息。 |
| changeReason | [AudioStreamDeviceChangeReason](arkts-apis-audio-e.md#audiostreamdevicechangereason11) | 否 | 否 | 流设备变更原因。 |

## CurrentOutputDeviceChangedEvent<sup>20+</sup>

应用接收到输出设备的变更事件。

**系统能力：** SystemCapability.Multimedia.Audio.Core

| 名称              | 类型                                                                | 只读 | 可选 | 说明               |
| :---------------- |:------------------------------------------------------------------| :--- |---| :----------------- |
| devices              | [AudioDeviceDescriptors](arkts-apis-audio-t.md#audiodevicedescriptors)                 | 否 | 否 | 设备信息。 |
| changeReason | [AudioStreamDeviceChangeReason](arkts-apis-audio-e.md#audiostreamdevicechangereason11) | 否 | 否 | 设备变更原因。 |
| recommendedAction | [OutputDeviceChangeRecommendedAction](arkts-apis-audio-e.md#outputdevicechangerecommendedaction20) | 否 | 否 | 设备变更后推荐的操作。 |

## AudioTimestampInfo<sup>19+</sup>

音频流时间戳和当前数据帧位置信息。

**系统能力：** SystemCapability.Multimedia.Audio.Core

| 名称 | 类型 | 只读 | 可选 | 说明                                |
| ---------| ------ | ---- | ---- |-----------------------------------|
| framePos | number | 是   | 否   | 当前播放或者录制的数据帧位置。                   |
| timestamp | number | 是   | 否   | 播放或者录制到当前数据帧位置时对应的时间戳。 |

## AudioCapturerInfo<sup>8+</sup>

描述音频采集器信息。

**系统能力：** SystemCapability.Multimedia.Audio.Core

| 名称          | 类型                      | 只读 | 可选 | 说明             |
| :------------ | :------------------------ | :--- |---| :--------------- |
| source        | [SourceType](arkts-apis-audio-e.md#sourcetype8) | 否 | 否 | 音源类型。       |
| capturerFlags | number                    | 否 | 否 | 音频采集器标志。<br>0代表音频采集器。 |

## AudioCapturerOptions<sup>8+</sup>

音频采集器选项信息。

| 名称                                | 类型                                                      | 只读 | 可选 | 说明                                                         |
| ----------------------------------- | --------------------------------------------------------- | ---- |---| ------------------------------------------------------------ |
| streamInfo                          | [AudioStreamInfo](#audiostreaminfo8)                      | 否 | 否 | 音频流信息。 <br/>**系统能力：** SystemCapability.Multimedia.Audio.Capturer   |
| capturerInfo                        | [AudioCapturerInfo](#audiocapturerinfo8)                   | 否 | 否 | 音频采集器信息。 <br/>**系统能力：** SystemCapability.Multimedia.Audio.Capturer        |
| playbackCaptureConfig<sup>(deprecated)</sup> | [AudioPlaybackCaptureConfig](#audioplaybackcaptureconfigdeprecated) | 否 | 是 | 音频内录的配置信息。<br/>**系统能力：** SystemCapability.Multimedia.Audio.PlaybackCapture<br/> 从API version 10开始支持，从API version 12开始废弃，建议使用[录屏接口AVScreenCapture](../apis-media-kit/capi-avscreencapture.md)替代。  |

## AudioInterrupt<sup>(deprecated)</sup>

音频监听事件传入的参数。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃，无替代接口。

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

| 名称            | 类型                        | 只读 | 可选 | 说明                                                         |
| --------------- | --------------------------- | ----|---| ------------------------------------------------------------ |
| streamUsage     | [StreamUsage](arkts-apis-audio-e.md#streamusage) | 否 | 否 | 音频流使用类型。                                             |
| contentType     | [ContentType](arkts-apis-audio-e.md#contenttypedeprecated) | 否 | 否 | 音频打断媒体类型。                                           |
| pauseWhenDucked | boolean                     | 否 | 否 | 音频打断时是否可以暂停音频播放。true表示音频播放可以在音频打断期间暂停，false表示音频播放不可以在音频打断期间暂停。 |

## CaptureFilterOptions<sup>(deprecated)</sup>

待录制的播放音频流的筛选信息。

> **说明：**
> 从API version 10开始支持，从API version 12开始废弃，建议使用[录屏接口AVScreenCapture](../apis-media-kit/capi-avscreencapture.md)替代。

**系统能力：** SystemCapability.Multimedia.Audio.PlaybackCapture

| 名称   | 类型                               | 只读 | 可选 | 说明                                                         |
| ------ | ---------------------------------- | ---- |---| ------------------------------------------------------------ |
| usages | Array\<[StreamUsage](arkts-apis-audio-e.md#streamusage)> | 否 | 否 | 指定需要录制的音频播放流的StreamUsage类型。可同时指定0个或多个StreamUsage。Array为空时，默认录制StreamUsage为STREAM_USAGE_MUSIC、STREAM_USAGE_MOVIE、STREAM_USAGE_GAME和STREAM_USAGE_AUDIOBOOK的音频播放流。<br>在API version 10时，CaptureFilterOptions支持使用StreamUsage.STREAM_USAGE_VOICE_COMMUNICATION，使用时需要申请权限ohos.permission.CAPTURE_VOICE_DOWNLINK_AUDIO，该权限仅系统应用可申请。<br>从API version 11开始，CaptureFilterOptions不再支持使用StreamUsage.STREAM_USAGE_VOICE_COMMUNICATION，所以当前接口不再涉及此权限。 |

## AudioPlaybackCaptureConfig<sup>(deprecated)</sup>

音频内录的配置信息。

> **说明：**
> 从API version 10开始支持，从API version 12开始废弃，建议使用[录屏接口AVScreenCapture](../apis-media-kit/capi-avscreencapture.md)替代。

**系统能力：** SystemCapability.Multimedia.Audio.PlaybackCapture

| 名称          | 类型                                          | 只读 | 可选 | 说明                             |
| ------------- | --------------------------------------------- | ---- |---| -------------------------------- |
| filterOptions | [CaptureFilterOptions](#capturefilteroptionsdeprecated) | 否 | 否 | 需要录制的播放音频流的筛选信息。 |

## InterruptAction<sup>(deprecated)</sup>

音频打断/获取焦点事件的回调方法。

> **说明：**
>
> 从API version 7开始支持，从API version 9开始废弃，建议使用[InterruptEvent](#interruptevent9)替代。

**系统能力：** SystemCapability.Multimedia.Audio.Renderer

| 名称       | 类型                                        | 只读 | 可选 | 说明                                                         |
| ---------- | ------------------------------------------- | ---- |---| ------------------------------------------------------------ |
| actionType | [InterruptActionType](arkts-apis-audio-e.md#interruptactiontypedeprecated) | 否 | 否 | 事件返回类型。TYPE_ACTIVATED为焦点触发事件，TYPE_INTERRUPT为音频打断事件。 |
| type       | [InterruptType](arkts-apis-audio-e.md#interrupttype)             | 否 | 是 | 打断事件类型。                                               |
| hint       | [InterruptHint](arkts-apis-audio-e.md#interrupthint)             | 否 | 是 | 打断事件提示。                                               |
| activated  | boolean                                     | 否 | 是 | 焦点获取/释放是否成功。true表示焦点获取/释放成功，false表示焦点获得/释放失败。 |
