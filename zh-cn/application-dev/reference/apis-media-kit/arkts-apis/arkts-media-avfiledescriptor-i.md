# AVFileDescriptor

Media file descriptor. The caller needs to ensure that the fd is valid and
the offset and length are correct.

**起始版本：** 9

**系统能力：** SystemCapability.Multimedia.Media.Core

## fd

```TypeScript
fd: number
```

The file descriptor of audio or video source from file system. The caller
is responsible to close the file descriptor.

**类型：** number

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

## length

```TypeScript
length?: number
```

The length in bytes of the data to be read. By default, the length is the
rest of bytes in the file from the offset.

**类型：** number

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

## offset

```TypeScript
offset?: number
```

The offset into the file where the data to be read, in bytes. By default,
the offset is zero.

**类型：** number

**起始版本：** 9

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Multimedia.Media.Core

