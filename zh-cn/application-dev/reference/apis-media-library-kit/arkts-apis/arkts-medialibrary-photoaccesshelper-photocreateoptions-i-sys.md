# PhotoCreateOptions（系统接口）

图片或视频的创建选项。

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## cameraShotKey

```TypeScript
cameraShotKey?: string
```

锁屏相机拍照或录像的标记字段（仅开放给系统相机,其key值由系统相机定义）。

**类型：** string

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## subtype

```TypeScript
subtype?: PhotoSubtype
```

图片或者视频的子类型。

**类型：** PhotoSubtype

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## userId

```TypeScript
userId?: number
```

用户id。

**类型：** number

**起始版本：** 19

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。
