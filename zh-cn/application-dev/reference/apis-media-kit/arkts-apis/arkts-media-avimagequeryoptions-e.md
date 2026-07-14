# AVImageQueryOptions

需要获取的缩略图时间点与视频帧的对应关系。

在获取视频缩略图时，传入的时间点与实际取得的视频帧所在时间点不一定相等，需要指定传入的时间点与实际取得的视频帧的时间关系。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Media.AVImageGenerator

## AV_IMAGE_QUERY_NEXT_SYNC

```TypeScript
AV_IMAGE_QUERY_NEXT_SYNC = 0
```

表示选取传入时间点或之后的关键帧。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Media.AVImageGenerator

## AV_IMAGE_QUERY_PREVIOUS_SYNC

```TypeScript
AV_IMAGE_QUERY_PREVIOUS_SYNC
```

表示选取传入时间点或之前的关键帧。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Media.AVImageGenerator

## AV_IMAGE_QUERY_CLOSEST_SYNC

```TypeScript
AV_IMAGE_QUERY_CLOSEST_SYNC
```

表示选取离传入时间点最近的关键帧。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Media.AVImageGenerator

## AV_IMAGE_QUERY_CLOSEST

```TypeScript
AV_IMAGE_QUERY_CLOSEST
```

表示选取离传入时间点最近的帧，该帧不一定是关键帧。

**起始版本：** 12

**系统能力：** SystemCapability.Multimedia.Media.AVImageGenerator

