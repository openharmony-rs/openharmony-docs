# PreferredCompatibleMode

枚举，根据配置的资产兼容性执行转码。

**起始版本：** 26.0.0

<!--Device-photoAccessHelper-enum PreferredCompatibleMode--><!--Device-photoAccessHelper-enum PreferredCompatibleMode-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## DEFAULT

```TypeScript
DEFAULT = 0
```

根据配置的资产兼容性功能执行转码。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PreferredCompatibleMode-DEFAULT = 0--><!--Device-PreferredCompatibleMode-DEFAULT = 0-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## CURRENT

```TypeScript
CURRENT = 1
```

不进行转码。资产将以其原始格式返回。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PreferredCompatibleMode-CURRENT = 1--><!--Device-PreferredCompatibleMode-CURRENT = 1-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## COMPATIBLE

```TypeScript
COMPATIBLE = 2
```

所有资产都被转码为最广泛兼容的格式(如JPEG)。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-PreferredCompatibleMode-COMPATIBLE = 2--><!--Device-PreferredCompatibleMode-COMPATIBLE = 2-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

