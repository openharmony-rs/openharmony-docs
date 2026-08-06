# AVRecorderConfig

音视频录制的参数。 audioSourceType和videoSourceType参数用于区分纯音频录制、纯视频录制和音视频录制。纯音频录制仅设置audioSourceType。纯视频录制仅设置videoSourceType。音视频录制需同时设置audioSourceType和videoSourceType。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-unnamed-interface AVRecorderConfig--><!--Device-unnamed-interface AVRecorderConfig-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## audioSourceType

```TypeScript
audioSourceType?: AudioSourceType
```

录制的音频源类型。录制音频时该参数为必填参数。\_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_**原子化服务API**：从API version 12开始，该接口支持在原子化服务中使用。

**类型：** AudioSourceType

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVRecorderConfig-audioSourceType?: AudioSourceType--><!--Device-AVRecorderConfig-audioSourceType?: AudioSourceType-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## fileGenerationMode

```TypeScript
fileGenerationMode?: FileGenerationMode
```

文件创建模式，与on('photoAssetAvailable')配合使用。

**类型：** FileGenerationMode

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-AVRecorderConfig-fileGenerationMode?: FileGenerationMode--><!--Device-AVRecorderConfig-fileGenerationMode?: FileGenerationMode-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## location

```TypeScript
location?: Location
```

录制视频的地理位置。默认不记录地理位置信息。\_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_此接口从API version 6开始支持，从API version 12开始废弃，建议使用**AVMetadata.location**替代。如果同时设置了两个参数，将使用**AVMetadata.location**。

**类型：** Location

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 12

**替代接口：** ohos.multimedia.media/media.AVMetadata#location

<!--Device-AVRecorderConfig-location?: Location--><!--Device-AVRecorderConfig-location?: Location-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## maxDuration

```TypeScript
maxDuration?: int
```

最大录制时长，单位为秒。取值范围为[1, 2^31-1]。如果提供了无效值，将重置为最大允许时长。一旦录制达到指定时长，将自动停止并通过**stateChange**回调通知录制已停止：AVRecorderState = 'stopped'，StateChangeReason = BACKGROUND。

**类型：** int

**起始版本：** 18

**ArkTS模式：** ArkTS-Dyn起始版本为18；ArkTS-Sta起始版本为23。

<!--Device-AVRecorderConfig-maxDuration?: int--><!--Device-AVRecorderConfig-maxDuration?: int-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## metadata

```TypeScript
metadata?: AVMetadata
```

元数据。详见AVMetadata。

**类型：** AVMetadata

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-AVRecorderConfig-metadata?: AVMetadata--><!--Device-AVRecorderConfig-metadata?: AVMetadata-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## profile

```TypeScript
profile: AVRecorderProfile
```

录制配置参数。此参数为必填参数。\_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_**原子化服务API**：从API version 12开始，该接口支持在原子化服务中使用。

**类型：** AVRecorderProfile

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVRecorderConfig-profile: AVRecorderProfile--><!--Device-AVRecorderConfig-profile: AVRecorderProfile-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## rotation

```TypeScript
rotation?: number
```

录制视频的旋转角度。MP4视频取值可为0（默认）、90、180或270。\_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_此接口从API version 6开始支持，从API version 12开始废弃，建议使用**AVMetadata.videoOrientation**替代。如果同时设置了两个参数，将使用**AVMetadata.videoOrientation**。

**类型：** number

**起始版本：** 9

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为9。

**废弃版本：** 12

**替代接口：** ohos.multimedia.media/media.AVMetadata#videoOrientation

<!--Device-AVRecorderConfig-rotation?: number--><!--Device-AVRecorderConfig-rotation?: number-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## url

```TypeScript
url: string
```

录制输出URL：fd://xx（fd句柄）。\_\_\_HTML\_TAG\_DESC\_USD\_0\_\_\_此参数为必填参数。\_\_\_HTML\_TAG\_DESC\_USD\_1\_\_\_**原子化服务API**：从API version 12开始，该接口支持在原子化服务中使用。

**类型：** string

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-AVRecorderConfig-url: string--><!--Device-AVRecorderConfig-url: string-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## videoSourceType

```TypeScript
videoSourceType?: VideoSourceType
```

录制的视频源类型。录制视频时该参数为必填参数。

**类型：** VideoSourceType

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-AVRecorderConfig-videoSourceType?: VideoSourceType--><!--Device-AVRecorderConfig-videoSourceType?: VideoSourceType-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

