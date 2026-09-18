# AudioRecorderConfig

Provides the audio recorder configuration definitions.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [AVRecorderConfig](arkts-media-media-avrecorderconfig-i.md)

**System capability:** SystemCapability.Multimedia.Media.AudioRecorder

## Modules to Import

```TypeScript
import { media } from '@kit.MediaKit';
```

## audioEncodeBitRate

```TypeScript
audioEncodeBitRate?: number
```

Audio encoding bit rate, in bit/s.

**Type:** number

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [audioBitrate](arkts-media-media-avrecorderprofile-i.md#audiobitrate)

**System capability:** SystemCapability.Multimedia.Media.AudioRecorder

## audioEncoder

```TypeScript
audioEncoder?: AudioEncoder
```

Audio encoding format. The default value is DEFAULT, it will be deprecated after API8. use "audioEncoderMime" instead.

**Type:** [AudioEncoder](arkts-media-media-audioencoder-e.md)

**Since:** 6

**Deprecated since:** 8

**Substitutes:** [audioEncoderMime](#audioencodermime)

**System capability:** SystemCapability.Multimedia.Media.AudioRecorder

## audioEncoderMime

```TypeScript
audioEncoderMime?: CodecMimeType
```

audio encoding format MIME. it used to replace audioEncoder.

**Type:** [CodecMimeType](arkts-media-media-codecmimetype-e.md)

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [audioCodec](arkts-media-media-avrecorderprofile-i.md#audiocodec)

**System capability:** SystemCapability.Multimedia.Media.AudioRecorder

## audioSampleRate

```TypeScript
audioSampleRate?: number
```

Audio sampling rate, in Hz.

**Type:** number

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [audioSampleRate](arkts-media-media-avrecorderprofile-i.md#audiosamplerate)

**System capability:** SystemCapability.Multimedia.Media.AudioRecorder

## fileFormat

```TypeScript
fileFormat?: ContainerFormatType
```

output file format. see @ContainerFormatType , it used to replace "format".

**Type:** [ContainerFormatType](arkts-media-media-containerformattype-e.md)

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [fileFormat](arkts-media-media-avrecorderprofile-i.md#fileformat)

**System capability:** SystemCapability.Multimedia.Media.AudioRecorder

## format

```TypeScript
format?: AudioOutputFormat
```

Audio output format. The default value is DEFAULT, it will be deprecated after API8. it will be replaced with "fileFormat".

**Type:** [AudioOutputFormat](arkts-media-media-audiooutputformat-e.md)

**Since:** 6

**Deprecated since:** 8

**Substitutes:** [fileFormat](#fileformat)

**System capability:** SystemCapability.Multimedia.Media.AudioRecorder

## location

```TypeScript
location?: Location
```

Geographical location information.

**Type:** [Location](arkts-media-media-location-i.md)

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [location](arkts-media-media-avmetadata-i.md#location)

**System capability:** SystemCapability.Multimedia.Media.AudioRecorder

## numberOfChannels

```TypeScript
numberOfChannels?: number
```

Number of audio channels.

**Type:** number

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [audioChannels](arkts-media-media-avrecorderprofile-i.md#audiochannels)

**System capability:** SystemCapability.Multimedia.Media.AudioRecorder

## uri

```TypeScript
uri: string
```

Audio output uri.support two kind of uri now. format like: scheme + "://" + "context". file: file://path fd: fd://fd

**Type:** string

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [url](arkts-media-media-avrecorderconfig-i.md#url)

**System capability:** SystemCapability.Multimedia.Media.AudioRecorder
