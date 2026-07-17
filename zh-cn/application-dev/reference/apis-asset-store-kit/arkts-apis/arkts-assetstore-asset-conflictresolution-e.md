# ConflictResolution

枚举，新增关键资产时的冲突（如：别名相同）处理策略。

**起始版本：** 11

<!--Device-asset-enum ConflictResolution--><!--Device-asset-enum ConflictResolution-End-->

**系统能力：** SystemCapability.Security.Asset

## OVERWRITE

```TypeScript
OVERWRITE = 0
```

覆盖原有的关键资产。

**起始版本：** 11

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-ConflictResolution-OVERWRITE = 0--><!--Device-ConflictResolution-OVERWRITE = 0-End-->

**系统能力：** SystemCapability.Security.Asset

## THROW_ERROR

```TypeScript
THROW_ERROR = 1
```

抛出异常，由业务进行后续处理。

**起始版本：** 11

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-ConflictResolution-THROW_ERROR = 1--><!--Device-ConflictResolution-THROW_ERROR = 1-End-->

**系统能力：** SystemCapability.Security.Asset

