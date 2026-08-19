# Progress（系统接口）

复制操作的进度信息。

**起始版本：** 26.0.0

<!--Device-photoAccessHelper-interface Progress--><!--Device-photoAccessHelper-interface Progress-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## processed

```TypeScript
readonly processed: int
```

复制操作中已处理的信息数量。

**类型：** int

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Progress-readonly processed: int--><!--Device-Progress-readonly processed: int-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## remain

```TypeScript
readonly remain: int
```

复制操作中剩余需要处理的信息数量。

**类型：** int

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-Progress-readonly remain: int--><!--Device-Progress-readonly remain: int-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

