# GridLevel

枚举类型，用于设置拉起picker后的宫格列数档位。

**起始版本：** 26.0.0

<!--Device-photoAccessHelper-export enum GridLevel--><!--Device-photoAccessHelper-export enum GridLevel-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## SPACIOUS

```TypeScript
SPACIOUS = 0
```

宽松宫格档位。该挡位为标准宫格的列数减1。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-GridLevel-SPACIOUS = 0--><!--Device-GridLevel-SPACIOUS = 0-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## STANDARD

```TypeScript
STANDARD = 1
```

标准宫格档位。不同设备尺寸对应的标准宫格列数各不相同，当未配置标准宫格列数时，系统将使用默认列数。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-GridLevel-STANDARD = 1--><!--Device-GridLevel-STANDARD = 1-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## COMPACT

```TypeScript
COMPACT = 2
```

紧密宫格档位。该挡位为标准宫格的列数加1。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-GridLevel-COMPACT = 2--><!--Device-GridLevel-COMPACT = 2-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

