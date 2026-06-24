# EncoderInfo

Describes the information about an encoder.

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## bitRate

```TypeScript
bitRate?: Range
```

Bit rate range of the encoder, with the minimum and maximum bit rates specified, in bit/s.

**类型：** Range

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## channels

```TypeScript
channels?: Range
```

Number of audio channels for the audio capturer, with the minimum and maximum numbers of audio channels
specified.
This parameter is available only for audio encoders.

**类型：** Range

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## frameRate

```TypeScript
frameRate?: Range
```

Video frame rate range, with the minimum and maximum frame rates specified, in fps.
This parameter is available only for video encoders.

**类型：** Range

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## height

```TypeScript
height?: Range
```

Video frame height range, with the minimum and maximum heights specified, in px.
This parameter is available only for video encoders.

**类型：** Range

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## mimeType

```TypeScript
mimeType: CodecMimeType
```

MIME type of the encoder.

**类型：** CodecMimeType

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## sampleRate

```TypeScript
sampleRate?: Array<number>
```

Audio sampling rate, including all available audio sampling rates, in Hz. The value depends on the encoder type,
and this parameter is available only for audio encoders.

**类型：** Array<number>

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## type

```TypeScript
type: string
```

Encoder type. The value **audio** means an audio encoder, and **video** means a video encoder.

**类型：** string

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

## width

```TypeScript
width?: Range
```

Video frame width range, with the minimum and maximum widths specified, in px.
This parameter is available only for video encoders.

**类型：** Range

**起始版本：** 11

**系统能力：** SystemCapability.Multimedia.Media.AVRecorder

