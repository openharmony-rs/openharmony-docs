# AVScreenCaptureRecordConfig

Defines the screen capture parameters.

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

## audioBitrate

```TypeScript
audioBitrate?: number
```

Audio bit rate, in bit/s. This value is used for both internal capture and external capture (using microphones).
The default value is **96000**.

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

## audioChannelCount

```TypeScript
audioChannelCount?: number
```

Number of audio channels. This value is used for both internal capture and external capture (using microphones).
Only **1** and **2** (default) are supported.

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

## audioSampleRate

```TypeScript
audioSampleRate?: number
```

Audio sampling rate, in Hz. This value is used for both internal capture
and external capture (using microphones), in Hz. Only **48000** (default value) and **16000** are supported.

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

## displayId

```TypeScript
displayId?: number
```

ID of the display used for screen capture. By default, the main screen is captured.

**类型：** number

**起始版本：** 15

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

## fd

```TypeScript
fd: number
```

FD of the file output.

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

## fillMode

```TypeScript
fillMode?: AVScreenCaptureFillMode
```

Video fill mode during screen capture.

**类型：** AVScreenCaptureFillMode

**起始版本：** 18

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

## frameHeight

```TypeScript
frameHeight?: number
```

Video height, in px. The default value varies according to the display in use.

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

## frameWidth

```TypeScript
frameWidth?: number
```

Video width, in px. The default value varies according to the display in use.

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

## preset

```TypeScript
preset?: AVScreenCaptureRecordPreset
```

Encoding and container format used. The default value is **SCREEN_RECORD_PRESET_H264_AAC_MP4**.

**类型：** AVScreenCaptureRecordPreset

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

## strategy

```TypeScript
strategy?: AVScreenCaptureStrategy
```

Screen Capture Policy Configuration Fields

**类型：** AVScreenCaptureStrategy

**默认值：** {default value of the property} [Required if provided]

**起始版本：** 20

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

## videoBitrate

```TypeScript
videoBitrate?: number
```

Video bit rate, in bit/s. The default value is **10000000**.

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Media.AVScreenCapture

