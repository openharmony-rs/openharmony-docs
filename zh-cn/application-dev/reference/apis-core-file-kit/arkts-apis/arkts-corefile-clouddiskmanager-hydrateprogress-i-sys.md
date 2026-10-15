# HydrateProgress（系统接口）

```TypeScript
interface HydrateProgress
```

封装水合进度信息。

**起始版本：** 26.0.1

<!--Device-cloudDiskManager-interface HydrateProgress--><!--Device-cloudDiskManager-interface HydrateProgress-End-->

**系统能力：** SystemCapability.FileManagement.CloudDiskManager

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { cloudDiskManager } from '@kit.CoreFileKit';
```

## filePath

```TypeScript
filePath: string
```

文件的原始绝对路径，与传入的占位符一致。最大长度为4096且不能为空。

**类型：** string

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HydrateProgress-filePath: string--><!--Device-HydrateProgress-filePath: string-End-->

**系统能力：** SystemCapability.FileManagement.CloudDiskManager

**系统接口：** 此接口为系统接口。

## processedSize

```TypeScript
processedSize: number
```

下载的字节数。仅当state为IN_PROGRESS时有效。单位为：字节。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HydrateProgress-processedSize: long--><!--Device-HydrateProgress-processedSize: long-End-->

**系统能力：** SystemCapability.FileManagement.CloudDiskManager

**系统接口：** 此接口为系统接口。

## state

```TypeScript
state: HydrateProgressState
```

水合物进展情况。

**类型：** [HydrateProgressState](arkts-corefile-clouddiskmanager-hydrateprogressstate-e-sys.md)

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HydrateProgress-state: HydrateProgressState--><!--Device-HydrateProgress-state: HydrateProgressState-End-->

**系统能力：** SystemCapability.FileManagement.CloudDiskManager

**系统接口：** 此接口为系统接口。

## totalSize

```TypeScript
totalSize: number
```

正在处理的文件的总大小，以字节为单位。单位为：字节。

**类型：** number

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-HydrateProgress-totalSize: long--><!--Device-HydrateProgress-totalSize: long-End-->

**系统能力：** SystemCapability.FileManagement.CloudDiskManager

**系统接口：** 此接口为系统接口。
