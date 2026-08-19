# PhotoCreateOptions（系统接口）

图片或视频的创建选项。

**起始版本：** 23

<!--Device-photoAccessHelper-interface PhotoCreateOptions--><!--Device-photoAccessHelper-interface PhotoCreateOptions-End-->

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

**起始版本：** 23

<!--Device-PhotoCreateOptions-cameraShotKey?: string--><!--Device-PhotoCreateOptions-cameraShotKey?: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## subtype

```TypeScript
subtype?: PhotoSubtype
```

图片或者视频的子类型。

**类型：** PhotoSubtype

**起始版本：** 23

<!--Device-PhotoCreateOptions-subtype?: PhotoSubtype--><!--Device-PhotoCreateOptions-subtype?: PhotoSubtype-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## userId

```TypeScript
userId?: int
```

用户id。

**类型：** int

**起始版本：** 23

<!--Device-PhotoCreateOptions-userId?: int--><!--Device-PhotoCreateOptions-userId?: int-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

