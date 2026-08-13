# FrameInfo

Defines the frame info when fetch picture form a video.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-media-interface FrameInfo--><!--Device-media-interface FrameInfo-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## actualTimeUs

```TypeScript
actualTimeUs?: long
```

The actual frame time.

**类型：** long

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameInfo-actualTimeUs?: long--><!--Device-FrameInfo-actualTimeUs?: long-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## image

```TypeScript
image?: image.PixelMap
```

The image extracted from video.

**类型：** image.PixelMap

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameInfo-image?: image.PixelMap--><!--Device-FrameInfo-image?: image.PixelMap-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## requestedTimeUs

```TypeScript
requestedTimeUs: long
```

The requested frame time.

**类型：** long

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameInfo-requestedTimeUs: long--><!--Device-FrameInfo-requestedTimeUs: long-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## result

```TypeScript
result: FetchResult
```

The fetch result code - succeed, failed or cancelled.

**类型：** [FetchResult](arkts-media-media-fetchresult-e.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FrameInfo-result: FetchResult--><!--Device-FrameInfo-result: FetchResult-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

