# RecommendationOptions

图片推荐选项(基于图片数据分析结果，依赖设备适配)。

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## defaultRecommendationType

```TypeScript
defaultRecommendationType?: RecommendationType
```

表示打开Picker直接显示的推荐标签。需要配置recommendationTypeList后，该配置才生效。

如果该标签存在，则默认显示该标签页。

如果该标签不存在，则默认显示“全部”标签页。

**类型：** [RecommendationType](arkts-medialibrary-photoaccesshelper-recommendationtype-e.md)

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## recommendationTypeList

```TypeScript
recommendationTypeList?: Array<RecommendationType>
```

如果需要根据枚举值同时推荐多个分类的图片，则配置此参数。

**类型：** Array&lt;[RecommendationType](arkts-medialibrary-photoaccesshelper-recommendationtype-e.md)&gt;

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。
