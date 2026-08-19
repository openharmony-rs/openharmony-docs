# PhotoCreationSource（系统接口）

代替应用创建资产传入的应用信息。

**起始版本：** 23

<!--Device-photoAccessHelper-interface PhotoCreationSource--><!--Device-photoAccessHelper-interface PhotoCreationSource-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## appId

```TypeScript
appId?: string
```

需保存图片/视频文件的app id。

**类型：** string

**起始版本：** 23

<!--Device-PhotoCreationSource-appId?: string--><!--Device-PhotoCreationSource-appId?: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## appName

```TypeScript
appName?: string
```

需保存图片/视频文件的app name。

**类型：** string

**起始版本：** 23

<!--Device-PhotoCreationSource-appName?: string--><!--Device-PhotoCreationSource-appName?: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## bundleName

```TypeScript
bundleName?: string
```

需保存图片/视频文件的应用bundle name。

**类型：** string

**起始版本：** 23

<!--Device-PhotoCreationSource-bundleName?: string--><!--Device-PhotoCreationSource-bundleName?: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## tokenId

```TypeScript
tokenId?: long
```

应用标识，将访问权限授予tokenId标识的应用。

**类型：** long

**起始版本：** 23

<!--Device-PhotoCreationSource-tokenId?: long--><!--Device-PhotoCreationSource-tokenId?: long-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

