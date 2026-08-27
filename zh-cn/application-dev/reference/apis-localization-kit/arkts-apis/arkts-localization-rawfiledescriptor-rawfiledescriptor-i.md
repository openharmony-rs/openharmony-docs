# RawFileDescriptor

本模块提供rawfile文件所在HAP包的文件描述符信息，包括文件描述符、rawfile文件的起始偏移和文件长度。

**起始版本：** 8

**系统能力：** SystemCapability.Global.ResourceManager

## fd

```TypeScript
fd: number
```

文件描述符。

**类型：** number

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

## length

```TypeScript
length: number
```

文件长度，表示rawfile文件的大小。单位为Byte。

**类型：** number

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager

## offset

```TypeScript
offset: number
```

起始偏移量，表示rawfile文件在HAP包中的起始位置。单位为Byte。

**类型：** number

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Global.ResourceManager
