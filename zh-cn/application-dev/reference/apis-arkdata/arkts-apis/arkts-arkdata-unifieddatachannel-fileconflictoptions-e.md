# FileConflictOptions

表示文件拷贝冲突时的可选策略的枚举。

**起始版本：** 15

<!--Device-unifiedDataChannel-enum FileConflictOptions--><!--Device-unifiedDataChannel-enum FileConflictOptions-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## OVERWRITE

```TypeScript
OVERWRITE = 0
```

目标路径存在同文件名时覆盖。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-FileConflictOptions-OVERWRITE = 0--><!--Device-FileConflictOptions-OVERWRITE = 0-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## SKIP

```TypeScript
SKIP = 1
```

目标路径存在同文件名时跳过。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本15开始，该接口支持在原子化服务API中使用。

<!--Device-FileConflictOptions-SKIP = 1--><!--Device-FileConflictOptions-SKIP = 1-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

