# HdrGainmapMetadata

Gainmap使用的元数据值，[HdrMetadataKey](arkts-image-image-hdrmetadatakey-e.md#HdrMetadataKey)中HDR_GAINMAP_METADATA关键字对应的值，参考ISO 21496-1。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-image-interface HdrGainmapMetadata--><!--Device-image-interface HdrGainmapMetadata-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## alternateHeadroom

```TypeScript
alternateHeadroom: double
```

The alternate hdr headroom.

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-HdrGainmapMetadata-alternateHeadroom: double--><!--Device-HdrGainmapMetadata-alternateHeadroom: double-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## baseHeadroom

```TypeScript
baseHeadroom: double
```

The baseline hdr headroom.

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-HdrGainmapMetadata-baseHeadroom: double--><!--Device-HdrGainmapMetadata-baseHeadroom: double-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## channels

```TypeScript
channels: Array<GainmapChannel>
```

The per-channel metadata.

**类型：** Array&lt;[GainmapChannel](arkts-image-image-gainmapchannel-i.md)&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-HdrGainmapMetadata-channels: Array<GainmapChannel>--><!--Device-HdrGainmapMetadata-channels: Array<GainmapChannel>-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## gainmapChannelCount

```TypeScript
gainmapChannelCount: int
```

The number of gain map channels, with a value of 1 or 3.

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-HdrGainmapMetadata-gainmapChannelCount: int--><!--Device-HdrGainmapMetadata-gainmapChannelCount: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## miniVersion

```TypeScript
miniVersion: int
```

The minimum version a parser needs to understand.

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-HdrGainmapMetadata-miniVersion: int--><!--Device-HdrGainmapMetadata-miniVersion: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## useBaseColorFlag

```TypeScript
useBaseColorFlag: boolean
```

Indicate whether to use the color space of the base image.

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-HdrGainmapMetadata-useBaseColorFlag: boolean--><!--Device-HdrGainmapMetadata-useBaseColorFlag: boolean-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

## writerVersion

```TypeScript
writerVersion: int
```

The version used by the writer.

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-HdrGainmapMetadata-writerVersion: int--><!--Device-HdrGainmapMetadata-writerVersion: int-End-->

**系统能力：** SystemCapability.Multimedia.Image.Core

