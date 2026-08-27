# ProgressIndicator

表示进度条指示选项的枚举，可选择是否采用系统默认进度显示。

**起始版本：** 15

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## NONE

```TypeScript
NONE = 0
```

不采用系统默认进度显示。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## DEFAULT

```TypeScript
DEFAULT = 1
```

采用系统默认进度显示，500ms内获取数据完成将不会拉起默认进度条。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core
