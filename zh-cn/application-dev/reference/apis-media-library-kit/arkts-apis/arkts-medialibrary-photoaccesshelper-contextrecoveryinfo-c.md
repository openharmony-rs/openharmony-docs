# ContextRecoveryInfo

介绍退出PhotoPicker的上下文信息。可以在后续的发射中使用 的PhotoPicker，以从上一个出口恢复状态。

**起始版本：** 26.0.0

<!--Device-photoAccessHelper-export class ContextRecoveryInfo--><!--Device-photoAccessHelper-export class ContextRecoveryInfo-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## albumUri

```TypeScript
albumUri: string
```

用户选择图片后，退出时的相册信息。 albumUri对应媒体库中相册的uri。 - 当上次在所有图片中选择时，albumUri为固定的"allPhotos"字符串。 - 当用户在搜索结果/文本推荐/头像推荐中完成选择退出时，不支持下次恢复现场，此时Picker返回的albumUri为空字符串。 默认值为空字符串。

**类型：** string

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ContextRecoveryInfo-albumUri: string--><!--Device-ContextRecoveryInfo-albumUri: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## displayName

```TypeScript
displayName: string
```

用户上次选择图片的宫格界面，左上角首张图片的文件名。默认为空字符串。

**类型：** string

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ContextRecoveryInfo-displayName: string--><!--Device-ContextRecoveryInfo-displayName: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## fileSize

```TypeScript
fileSize?: int
```

用户上次选择图片的宫格界面中，左上角首张图片的文件大小，默认为0。 单位为： Byte，取值应为≥0的整数。

**类型：** int

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ContextRecoveryInfo-fileSize?: int--><!--Device-ContextRecoveryInfo-fileSize?: int-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## gridLevel

```TypeScript
gridLevel?: GridLevel
```

用户上次退出宫格时的档位。

**类型：** [GridLevel](arkts-medialibrary-photoaccesshelper-gridlevel-e.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ContextRecoveryInfo-gridLevel?: GridLevel--><!--Device-ContextRecoveryInfo-gridLevel?: GridLevel-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## recommendationType

```TypeScript
recommendationType: int
```

用户上次选择时设置的推荐内容枚举值，参考[RecommendationType](arkts-medialibrary-photoaccesshelper-recommendationtype-e.md)值定义。 上次选择时未设置推荐时，默认为0。

**类型：** int

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ContextRecoveryInfo-recommendationType: int--><!--Device-ContextRecoveryInfo-recommendationType: int-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## selectedRecommendationType

```TypeScript
selectedRecommendationType: int
```

用户上次选择时选中的推荐内容枚举值，参考[RecommendationType](arkts-medialibrary-photoaccesshelper-recommendationtype-e.md)值定义。 当上次选择未选中推荐项，选中"全部"时，默认为0。

**类型：** int

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ContextRecoveryInfo-selectedRecommendationType: int--><!--Device-ContextRecoveryInfo-selectedRecommendationType: int-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## sortRule

```TypeScript
sortRule?: string
```

用户上次选择图片的宫格界面的排序规则，默认为空字符串。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ContextRecoveryInfo-sortRule?: string--><!--Device-ContextRecoveryInfo-sortRule?: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## time

```TypeScript
time: long
```

用户上次选择图片的宫格界面，左上角首张图片的时间。 - 按拍摄时间排序的相册，返回拍摄时间。 - 按保存时间排序的相册返回保存时间。默认为0。 单位为： ms，取值应≥0。

**类型：** long

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ContextRecoveryInfo-time: long--><!--Device-ContextRecoveryInfo-time: long-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## version

```TypeScript
version: int
```

现场数据版本号，用于校验现场信息数据与现场恢复能力的匹配度。 版本号必须大于等于1.0。

**类型：** int

**起始版本：** 26.0.0

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ContextRecoveryInfo-version: int--><!--Device-ContextRecoveryInfo-version: int-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

