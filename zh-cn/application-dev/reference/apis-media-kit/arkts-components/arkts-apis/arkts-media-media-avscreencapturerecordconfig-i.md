# AVScreenCaptureRecordConfig

表示录屏参数配置。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## audioBitrate

```TypeScript
audioBitrate?: number
```

录屏的音频比特率，内录的系统音和外录的麦克风都使用此比特率，默认96000。单位为比特每秒（bit/s）。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

## audioChannelCount

```TypeScript
audioChannelCount?: number
```

录屏的音频通道数，内录的系统音和外录的麦克风都使用此通道数，默认2声道，仅支持设置1或2声道。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

## audioSampleRate

```TypeScript
audioSampleRate?: number
```

录屏的音频采样率。内录的系统音和外录的麦克风都使用此采样率，默认48000，仅支持设置48000或16000。单位为赫兹（Hz）。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

## displayId

```TypeScript
displayId?: number
```

指定录屏使用的屏幕，默认主屏幕。

**类型：** number

**起始版本：** 15

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

## fd

```TypeScript
fd: number
```

录制输出的文件fd。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

## fillMode

```TypeScript
fillMode?: AVScreenCaptureFillMode
```

录屏时视频流的填充模式。

**类型：** [AVScreenCaptureFillMode](arkts-media-media-avscreencapturefillmode-e.md)

**起始版本：** 18

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

## frameHeight

```TypeScript
frameHeight?: number
```

录屏的视频高度。默认屏幕高度，根据不同屏幕默认值不同。单位为像素（px）。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

## frameWidth

```TypeScript
frameWidth?: number
```

录屏的视频宽度。默认屏幕宽度，根据不同屏幕默认值不同。单位为像素（px）。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

## preset

```TypeScript
preset?: AVScreenCaptureRecordPreset
```

录屏使用的编码和封装格式，默认SCREEN_RECORD_PRESET_H264_AAC_MP4格式。

**类型：** [AVScreenCaptureRecordPreset](arkts-media-media-avscreencapturerecordpreset-e.md)

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

## strategy

```TypeScript
strategy?: AVScreenCaptureStrategy
```

录屏策略。

**类型：** [AVScreenCaptureStrategy](arkts-media-media-avscreencapturestrategy-i.md)

**默认值：** {default value of the property} [Required if provided]

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

## videoBitrate

```TypeScript
videoBitrate?: number
```

录屏的视频比特率。默认为10000000。单位为比特每秒（bit/s）。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture
