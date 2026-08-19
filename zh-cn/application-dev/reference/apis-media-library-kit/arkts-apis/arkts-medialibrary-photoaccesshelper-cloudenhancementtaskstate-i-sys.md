# CloudEnhancementTaskState（系统接口）

云增强任务状态，应用调用云增强任务查询接口的返回类型，包含云增强任务状态及部分状态下的额外信息。

**起始版本：** 23

<!--Device-photoAccessHelper-interface CloudEnhancementTaskState--><!--Device-photoAccessHelper-interface CloudEnhancementTaskState-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## expectedDuration

```TypeScript
readonly expectedDuration?: int
```

排队时间，单位：毫秒。当taskStage为CloudEnhancementTaskStage.TASK_STAGE_EXECUTING时提供。

**类型：** int

**起始版本：** 23

<!--Device-CloudEnhancementTaskState-readonly expectedDuration?: int--><!--Device-CloudEnhancementTaskState-readonly expectedDuration?: int-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## statusCode

```TypeScript
readonly statusCode?: int
```

状态码。当taskStage为CloudEnhancementTaskStage.TASK_STAGE_FAILED时提供。

**类型：** int

**起始版本：** 23

<!--Device-CloudEnhancementTaskState-readonly statusCode?: int--><!--Device-CloudEnhancementTaskState-readonly statusCode?: int-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## taskStage

```TypeScript
readonly taskStage: CloudEnhancementTaskStage
```

云增强任务状态。

**类型：** [CloudEnhancementTaskStage](arkts-medialibrary-photoaccesshelper-cloudenhancementtaskstage-e-sys.md)

**起始版本：** 23

<!--Device-CloudEnhancementTaskState-readonly taskStage: CloudEnhancementTaskStage--><!--Device-CloudEnhancementTaskState-readonly taskStage: CloudEnhancementTaskStage-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## totalFileSize

```TypeScript
readonly totalFileSize?: int
```

总文件大小，单位：字节。当taskStage为CloudEnhancementTaskStage.TASK_STAGE_UPLOADING或者 CloudEnhancementTaskStage.TASK_STAGE_DOWNLOADING时提供。

**类型：** int

**起始版本：** 23

<!--Device-CloudEnhancementTaskState-readonly totalFileSize?: int--><!--Device-CloudEnhancementTaskState-readonly totalFileSize?: int-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## transferredFileSize

```TypeScript
readonly transferredFileSize?: int
```

已传输的文件大小，单位：字节。当taskStage为CloudEnhancementTaskStage.TASK_STAGE_UPLOADING或者 CloudEnhancementTaskStage.TASK_STAGE_DOWNLOADING时提供。

**类型：** int

**起始版本：** 23

<!--Device-CloudEnhancementTaskState-readonly transferredFileSize?: int--><!--Device-CloudEnhancementTaskState-readonly transferredFileSize?: int-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

