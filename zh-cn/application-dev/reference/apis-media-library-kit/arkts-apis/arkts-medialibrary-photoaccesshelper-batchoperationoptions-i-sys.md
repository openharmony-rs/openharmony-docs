# BatchOperationOptions（系统接口）

批量复制操作选项。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## countProgressListener

```TypeScript
countProgressListener?: ProgressListener
```

复制操作的数量进度监听器。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## resultListener

```TypeScript
resultListener?: ResultListener
```

复制操作的结果监听器。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## sizeProgressListener

```TypeScript
sizeProgressListener?: ProgressListener
```

复制操作的大小进度监听器。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## mode

```TypeScript
mode?: number
```

复制操作的自动重命名模式。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## taskSignal

```TypeScript
taskSignal?: TaskSignal
```

复制操作的中断信号。

**类型：** TaskSignal

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。
