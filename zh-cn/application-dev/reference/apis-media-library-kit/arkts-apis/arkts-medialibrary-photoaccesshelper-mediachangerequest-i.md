# MediaChangeRequest

媒体变更请求，资产变更请求和相册变更请求的父类型。 > **注意**： > > 媒体变更请求需要在调用[applyChanges](arkts-medialibrary-photoaccesshelper-photoaccesshelper-i.md#applychanges)后才会 > 提交生效。

**起始版本：** 23

<!--Device-photoAccessHelper-interface MediaChangeRequest--><!--Device-photoAccessHelper-interface MediaChangeRequest-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## comment

```TypeScript
readonly comment: string
```

用于MediaChangeRequest类型校验。 如果类（如[MediaAssetChangeRequest](arkts-medialibrary-photoaccesshelper-mediaassetchangerequest-c.md)或 [MediaAlbumChangeRequest](arkts-medialibrary-photoaccesshelper-mediaalbumchangerequest-c.md)）对象可以访问，就说明该类是MediaChangeRequest的实现类。

**类型：** string

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-MediaChangeRequest-readonly comment: string--><!--Device-MediaChangeRequest-readonly comment: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

