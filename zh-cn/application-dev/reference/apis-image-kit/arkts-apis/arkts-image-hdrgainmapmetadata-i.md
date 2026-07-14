# HdrGainmapMetadata

Gainmap使用的元数据值，[HdrMetadataKey](arkts-image-hdrmetadatakey-e.md)中HDR_GAINMAP_METADATA关键字对应的值，参考ISO 21496-1。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## alternateHeadroom

```TypeScript
alternateHeadroom: number
```

The alternate hdr headroom.

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## baseHeadroom

```TypeScript
baseHeadroom: number
```

The baseline hdr headroom.

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## channels

```TypeScript
channels: Array<GainmapChannel>
```

The per-channel metadata.

**类型：** Array<GainmapChannel>

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## gainmapChannelCount

```TypeScript
gainmapChannelCount: number
```

The number of gain map channels, with a value of 1 or 3.

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## miniVersion

```TypeScript
miniVersion: number
```

The minimum version a parser needs to understand.

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## useBaseColorFlag

```TypeScript
useBaseColorFlag: boolean
```

Indicate whether to use the color space of the base image.

**类型：** boolean

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

## writerVersion

```TypeScript
writerVersion: number
```

The version used by the writer.

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Image.Core

