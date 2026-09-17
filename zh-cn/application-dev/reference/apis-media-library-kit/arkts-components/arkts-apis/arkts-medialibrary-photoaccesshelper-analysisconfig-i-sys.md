# AnalysisConfig（系统接口）

资产分析配置。

**起始版本：** 24

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## extraInfos

```TypeScript
extraInfos?: string
```

JSON字符串格式的扩展信息。

长度范围：(0, 500]。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## types

```TypeScript
types: AnalysisType[]
```

智慧分析类型数组，数组大小上限为[AnalysisType](arkts-medialibrary-photoaccesshelper-analysistype-e-sys.md)枚举定义成员数量。

**类型：** [AnalysisType](arkts-medialibrary-photoaccesshelper-analysistype-e-sys.md)[]

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## uris

```TypeScript
uris: string[]
```

资产URI数组。

长度范围：[0, 100]。

**类型：** string[]

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。
