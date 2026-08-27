# DeepOptimizeSpaceProgress（系统接口）

深度优化存储空间的进度信息。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## progress

```TypeScript
progress: number
```

深度优化进度百分比。取值范围为[0, 100]。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## state

```TypeScript
state: DeepOptimizeState
```

当前深度优化状态。

**类型：** [DeepOptimizeState](arkts-medialibrary-photoaccesshelper-deepoptimizestate-e-sys.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。
