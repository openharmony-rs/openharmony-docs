# PhotoAssetCustomRecord（系统接口）

媒体库支持图库自定义用户统计行为。

**起始版本：** 23

<!--Device-photoAccessHelper-interface PhotoAssetCustomRecord--><!--Device-photoAccessHelper-interface PhotoAssetCustomRecord-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## fileId

```TypeScript
readonly fileId: int
```

图片id，必须为大于0的整数。

**类型：** int

**起始版本：** 23

<!--Device-PhotoAssetCustomRecord-readonly fileId: int--><!--Device-PhotoAssetCustomRecord-readonly fileId: int-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## lcdJumpCount

```TypeScript
readonly lcdJumpCount: int
```

大图跳转分享等次数，必须为大于0的整数。

**类型：** int

**起始版本：** 23

<!--Device-PhotoAssetCustomRecord-readonly lcdJumpCount: int--><!--Device-PhotoAssetCustomRecord-readonly lcdJumpCount: int-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## shareCount

```TypeScript
readonly shareCount: int
```

图片和视频被分享的次数，必须为大于0的整数。

**类型：** int

**起始版本：** 23

<!--Device-PhotoAssetCustomRecord-readonly shareCount: int--><!--Device-PhotoAssetCustomRecord-readonly shareCount: int-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

