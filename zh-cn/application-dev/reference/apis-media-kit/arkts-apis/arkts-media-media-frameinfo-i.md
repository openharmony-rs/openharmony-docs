# FrameInfo

批量获取视频缩略图操作的返回值，包含请求抽帧的时间点、实际抽帧的时间点、从视频中输出缩略图的格式参数和获取单张缩略图操作的结果。

**起始版本：** 23

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## 导入模块

```TypeScript
import { media } from '@kit.MediaKit';
```

## actualTimeUs

```TypeScript
actualTimeUs?: number
```

实际抽帧的时间点。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## image

```TypeScript
image?: image.PixelMap
```

从视频中输出缩略图的格式参数。

**类型：** image.PixelMap

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## requestedTimeUs

```TypeScript
requestedTimeUs: number
```

请求抽帧的时间点。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor

## result

```TypeScript
result: FetchResult
```

获取单张缩略图任务的结果。例如成功，失败或任务被取消。

**类型：** FetchResult

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Multimedia.Media.AVMetadataExtractor
