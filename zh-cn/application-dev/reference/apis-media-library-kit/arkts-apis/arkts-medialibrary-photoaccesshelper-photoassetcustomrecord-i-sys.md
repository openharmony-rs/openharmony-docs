# PhotoAssetCustomRecord（系统接口）

媒体库支持图库自定义用户统计行为。

**起始版本：** 20

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## fileId

```TypeScript
readonly fileId: number
```

图片id，必须为大于0的整数。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## lcdJumpCount

```TypeScript
readonly lcdJumpCount: number
```

大图跳转分享等次数，必须为大于0的整数。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## shareCount

```TypeScript
readonly shareCount: number
```

图片和视频被分享的次数，必须为大于0的整数。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。
