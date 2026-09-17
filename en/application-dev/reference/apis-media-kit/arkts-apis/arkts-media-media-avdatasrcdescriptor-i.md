# AVDataSrcDescriptor

Defines the descriptor of an audio and video file, which is used in DataSource playback mode. Use scenario: An application can create a playback instance and start playback before it finishes downloading the audio and video resources.

**Since:** 10

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

## Modules to Import

```TypeScript
import { media } from '@kit.MediaKit';
```

## callback

```TypeScript
callback: (buffer: ArrayBuffer, length: number, pos?: number) => number
```

Callback function implemented by users, which is used to fill data. buffer - The buffer need to fill. length - The stream length player want to get. pos - The stream position player want get start, and is an optional parameter. When fileSize set to -1, this parameter is not used. Returns length of the data to be filled, Return -1 to indicate that the end of the stream is reached, Return -2 to indicate that an unrecoverable error has been encountered.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| buffer | ArrayBuffer | Yes |  |
| length | number | Yes |  |
| pos | number | No |  |

## fileSize

```TypeScript
fileSize: number
```

Size of the file, -1 means the file size is unknown, in this case, seek and setSpeed can't be executed, loop can't be set, and can't replay.

**Type:** number

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Multimedia.Media.AVPlayer
