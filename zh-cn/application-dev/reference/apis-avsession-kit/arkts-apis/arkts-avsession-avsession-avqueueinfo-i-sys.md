# AVQueueInfo（系统接口）

歌单（歌曲列表）的相关属性。

**起始版本：** 11

<!--Device-avSession-interface AVQueueInfo--><!--Device-avSession-interface AVQueueInfo-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { avSession } from '@kit.AVSessionKit';
```

## avQueueId

```TypeScript
avQueueId: string
```

歌单（歌曲列表）唯一标识Id。

**类型：** string

**起始版本：** 11

<!--Device-AVQueueInfo-avQueueId: string--><!--Device-AVQueueInfo-avQueueId: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**系统接口：** 此接口为系统接口。

## avQueueImage

```TypeScript
avQueueImage: image.PixelMap | string
```

歌单（歌曲列表）封面图，图片的像素数据或者图片路径地址（本地路径或网络路径）。

**类型：** image.PixelMap | string

**起始版本：** 11

<!--Device-AVQueueInfo-avQueueImage: image.PixelMap | string--><!--Device-AVQueueInfo-avQueueImage: image.PixelMap | string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**系统接口：** 此接口为系统接口。

## avQueueName

```TypeScript
avQueueName: string
```

歌单（歌曲列表）名称。

**类型：** string

**起始版本：** 11

<!--Device-AVQueueInfo-avQueueName: string--><!--Device-AVQueueInfo-avQueueName: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**系统接口：** 此接口为系统接口。

## bundleName

```TypeScript
bundleName: string
```

歌单所属应用包名。

**类型：** string

**起始版本：** 11

<!--Device-AVQueueInfo-bundleName: string--><!--Device-AVQueueInfo-bundleName: string-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**系统接口：** 此接口为系统接口。

## lastPlayedTime

```TypeScript
lastPlayedTime?: number
```

歌单最后播放时间。

**类型：** number

**起始版本：** 11

<!--Device-AVQueueInfo-lastPlayedTime?: long--><!--Device-AVQueueInfo-lastPlayedTime?: long-End-->

**系统能力：** SystemCapability.Multimedia.AVSession.Core

**系统接口：** 此接口为系统接口。

