# PixelMapParams

Defines the format parameters of the video thumbnail to be obtained.

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-media-interface PixelMapParams--><!--Device-media-interface PixelMapParams-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVImageGenerator

## height

```TypeScript
height?: int
```

Height of the thumbnail. Unit: px. The value must be greater than 0 and less than or equal to the height of the original video. Otherwise, the returned thumbnail will not be scaled.

**类型：** int

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-PixelMapParams-height?: int--><!--Device-PixelMapParams-height?: int-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVImageGenerator

## width

```TypeScript
width?: int
```

Width of the thumbnail. Unit: px. The value must be greater than 0 and less than or equal to the width of the original video. Otherwise, the returned thumbnail will not be scaled.

**类型：** int

**起始版本：** 12

**ArkTS模式：** ArkTS-Dyn起始版本为12；ArkTS-Sta起始版本为23。

<!--Device-PixelMapParams-width?: int--><!--Device-PixelMapParams-width?: int-End-->

**系统能力：** SystemCapability.Multimedia.Media.AVImageGenerator

