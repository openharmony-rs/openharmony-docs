# RecommendationOptions

图片推荐选项(基于图片数据分析结果，依赖设备适配)。

**起始版本：** 26.0.0

<!--Device-photoAccessHelper-class RecommendationOptions--><!--Device-photoAccessHelper-class RecommendationOptions-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## recommendationType

```TypeScript
recommendationType?: RecommendationType
```

如果需要根据枚举值推荐相应的图片，则配置此参数。

**类型：** [RecommendationType](arkts-medialibrary-photoaccesshelper-recommendationtype-e.md)

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-RecommendationOptions-recommendationType?: RecommendationType--><!--Device-RecommendationOptions-recommendationType?: RecommendationType-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## textContextInfo

```TypeScript
textContextInfo?: TextContextInfo
```

如果需要根据文本信息推荐相应的图片，则配置此参数（如果同时配置了recommendationType，则仅textContextInfo生效）。

**类型：** [TextContextInfo](arkts-medialibrary-photoaccesshelper-textcontextinfo-i.md)

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-RecommendationOptions-textContextInfo?: TextContextInfo--><!--Device-RecommendationOptions-textContextInfo?: TextContextInfo-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

