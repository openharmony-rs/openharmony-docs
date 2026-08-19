# DeepOptimizeSpaceProgress（系统接口）

深度优化存储空间的进度信息。

**起始版本：** 26.0.0

<!--Device-photoAccessHelper-interface DeepOptimizeSpaceProgress--><!--Device-photoAccessHelper-interface DeepOptimizeSpaceProgress-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## progress

```TypeScript
progress: int
```

深度优化进度百分比。取值范围为[0, 100]。

**类型：** int

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DeepOptimizeSpaceProgress-progress: int--><!--Device-DeepOptimizeSpaceProgress-progress: int-End-->

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

<!--Device-DeepOptimizeSpaceProgress-state: DeepOptimizeState--><!--Device-DeepOptimizeSpaceProgress-state: DeepOptimizeState-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

