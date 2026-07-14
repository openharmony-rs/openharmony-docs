# AVDataSrcDescriptor

Defines the descriptor of an audio and video file, which is used in DataSource playback mode.
Use scenario: An application can create a playback instance and start playback before it finishes
downloading the audio and video resources.

**起始版本：** 10

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

## callback

```TypeScript
callback: (buffer: ArrayBuffer, length: number, pos?: number) => number
```

Callback function implemented by users, which is used to fill data.
buffer - The buffer need to fill.
length - The stream length player want to get.
pos - The stream position player want get start, and is an optional parameter.
When fileSize set to -1, this parameter is not used.
Returns length of the data to be filled, Return -1 to indicate that the end of the stream is reached,
Return -2 to indicate that an unrecoverable error has been encountered.

**类型：** (buffer: ArrayBuffer, length: number, pos?: number) => number

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

## fileSize

```TypeScript
fileSize: number
```

Size of the file, -1 means the file size is unknown, in this case,
seek and setSpeed can't be executed, loop can't be set, and can't replay.

**类型：** number

**起始版本：** 10

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.AVPlayer

