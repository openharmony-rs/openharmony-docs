# AVScreenCaptureRecordConfig

Defines the screen capture parameters.

**Since:** 12

**System capability:** SystemCapability.Multimedia.Media.AVScreenCapture

## Modules to Import

```TypeScript
import { media } from '@kit.MediaKit';
```

## audioBitrate

```TypeScript
audioBitrate?: number
```

Audio bit rate, in bit/s. This value is used for both internal capture and external capture (using microphones). The default value is **96000**.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.Multimedia.Media.AVScreenCapture

## audioChannelCount

```TypeScript
audioChannelCount?: number
```

Number of audio channels. This value is used for both internal capture and external capture (using microphones). Only **1** and **2** (default) are supported.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.Multimedia.Media.AVScreenCapture

## audioSampleRate

```TypeScript
audioSampleRate?: number
```

Audio sampling rate, in Hz. This value is used for both internal capture and external capture (using microphones), in Hz. Only **48000** (default value) and **16000** are supported.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.Multimedia.Media.AVScreenCapture

## displayId

```TypeScript
displayId?: number
```

ID of the display used for screen capture. By default, the main screen is captured.

**Type:** number

**Since:** 15

**System capability:** SystemCapability.Multimedia.Media.AVScreenCapture

## fd

```TypeScript
fd: number
```

FD of the file output.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.Multimedia.Media.AVScreenCapture

## fillMode

```TypeScript
fillMode?: AVScreenCaptureFillMode
```

Video fill mode during screen capture.

**Type:** [AVScreenCaptureFillMode](arkts-media-media-avscreencapturefillmode-e.md)

**Since:** 18

**System capability:** SystemCapability.Multimedia.Media.AVScreenCapture

## frameHeight

```TypeScript
frameHeight?: number
```

Video height, in px. The default value varies according to the display in use.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.Multimedia.Media.AVScreenCapture

## frameWidth

```TypeScript
frameWidth?: number
```

Video width, in px. The default value varies according to the display in use.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.Multimedia.Media.AVScreenCapture

## preset

```TypeScript
preset?: AVScreenCaptureRecordPreset
```

Encoding and container format used. The default value is **SCREEN_RECORD_PRESET_H264_AAC_MP4**.

**Type:** [AVScreenCaptureRecordPreset](arkts-media-media-avscreencapturerecordpreset-e.md)

**Since:** 12

**System capability:** SystemCapability.Multimedia.Media.AVScreenCapture

## strategy

```TypeScript
strategy?: AVScreenCaptureStrategy
```

Screen Capture Policy Configuration Fields

**Type:** [AVScreenCaptureStrategy](arkts-media-media-avscreencapturestrategy-i.md)

**Default:** {default value of the property} [Required if provided]

**Since:** 20

**System capability:** SystemCapability.Multimedia.Media.AVScreenCapture

## videoBitrate

```TypeScript
videoBitrate?: number
```

Video bit rate, in bit/s. The default value is **10000000**.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.Multimedia.Media.AVScreenCapture
