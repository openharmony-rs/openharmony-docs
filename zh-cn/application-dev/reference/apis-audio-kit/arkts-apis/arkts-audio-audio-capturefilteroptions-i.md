# CaptureFilterOptions

```TypeScript
interface CaptureFilterOptions
```

待录制的播放音频流的筛选信息。

> **说明：** 
> 
> 从API version 10开始支持，从API version 12开始废弃，建议使用
> [录屏接口AVScreenCapture](../../../reference/apis-media-kit/capi-avscreencapture.md)替代。

**起始版本：** 10

**废弃版本：** 12

**替代接口：** OH_AVScreenCapture in native interface.

**系统能力：** SystemCapability.Multimedia.Audio.PlaybackCapture

## 导入模块

```TypeScript
import { audio } from '@kit.AudioKit';
```

## usages

```TypeScript
usages: Array<StreamUsage>
```

指定需要录制的音频播放流的StreamUsage类型。可同时指定0个或多个StreamUsage。Array为空时，默认录制StreamUsage为STREAM_USAGE_MUSIC、STREAM_USAGE_MOVIE、STREAM_USAGE_GAME和STREAM_USAGE_AUDIOBOOK的音频播放流。

在API version 10时，CaptureFilterOptions支持使用StreamUsage.STREAM_USAGE_VOICE_COMMUNICATION，使用时需要申请权限ohos.permission.CAPTURE_VOICE_DOWNLINK_AUDIO，该权限仅系统应用可申请。

从API version 11开始，CaptureFilterOptions不再支持使用StreamUsage.STREAM_USAGE_VOICE_COMMUNICATION，所以当前接口不再涉及此权限。

**类型：** Array&lt;[StreamUsage](arkts-audio-audio-streamusage-e.md)&gt;

**起始版本：** 10

**废弃版本：** 12

**替代接口：** OH_AVScreenCapture in native interface.

**需要权限：** 
- API版本11+：N/A
- API版本10：ohos.permission.CAPTURE_VOICE_DOWNLINK_AUDIO

**系统能力：** SystemCapability.Multimedia.Audio.PlaybackCapture
