# DefaultCoverOrderInfo（系统接口）

相册默认封面选择规则信息。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## albumSubtype

```TypeScript
public albumSubtype: AlbumSubtype
```

相册子类型。

**类型：** AlbumSubtype

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## albumType

```TypeScript
public albumType: AlbumType
```

相册类型。

**类型：** AlbumType

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## lpath

```TypeScript
public lpath?: string
```

相册的虚拟路径。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## orderKey

```TypeScript
public orderKey: PhotoKeys
```

默认封面选择依赖的主字段。

**类型：** [PhotoKeys](arkts-medialibrary-photoaccesshelper-photokeys-e.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## orderSubKey

```TypeScript
public orderSubKey: PhotoKeys
```

默认封面选择依赖的辅助字段。

**类型：** [PhotoKeys](arkts-medialibrary-photoaccesshelper-photokeys-e.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## orderType

```TypeScript
public orderType: number
```

默认封面选择依赖字段的排序类型。 值为整数，取值范围为[0, 1]。0表示按照orderKey和orderSubKey字段降序排列选择默认封面，1表示按照orderKey和orderSubKey字段升序排列选择默认封面。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。
