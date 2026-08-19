# MediaLibraryAvailability

媒体库可用性信息。

**起始版本：** 26.0.0

<!--Device-photoAccessHelper-interface MediaLibraryAvailability--><!--Device-photoAccessHelper-interface MediaLibraryAvailability-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## availabilityStatus

```TypeScript
availabilityStatus: AvailabilityStatus
```

媒体库可用性状态。

**类型：** [AvailabilityStatus](arkts-medialibrary-photoaccesshelper-availabilitystatus-e.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MediaLibraryAvailability-availabilityStatus: AvailabilityStatus--><!--Device-MediaLibraryAvailability-availabilityStatus: AvailabilityStatus-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## unavailabilityReason

```TypeScript
unavailabilityReason: string
```

媒体库不可用原因，例如"Database corrupted"。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-MediaLibraryAvailability-unavailabilityReason: string--><!--Device-MediaLibraryAvailability-unavailabilityReason: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

