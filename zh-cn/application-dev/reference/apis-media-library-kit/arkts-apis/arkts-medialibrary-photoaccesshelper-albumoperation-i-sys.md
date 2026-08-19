# AlbumOperation（系统接口）

相册操作信息。

**起始版本：** 26.0.0

<!--Device-photoAccessHelper-interface AlbumOperation--><!--Device-photoAccessHelper-interface AlbumOperation-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## attr

```TypeScript
attr: AlbumAttribute
```

设置相册的属性类型。

**类型：** [AlbumAttribute](arkts-medialibrary-photoaccesshelper-albumattribute-e-sys.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AlbumOperation-attr: AlbumAttribute--><!--Device-AlbumOperation-attr: AlbumAttribute-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## type

```TypeScript
type: AlbumOperationType
```

设置相册属性的操作类型。

**类型：** [AlbumOperationType](arkts-medialibrary-photoaccesshelper-albumoperationtype-e-sys.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AlbumOperation-type: AlbumOperationType--><!--Device-AlbumOperation-type: AlbumOperationType-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## values

```TypeScript
values: string[]
```

设置相册属性的字符串参数。数组最大长度为20；数组中的每个字符串长度不超过500个字符。

**类型：** string[]

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AlbumOperation-values: string[]--><!--Device-AlbumOperation-values: string[]-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

