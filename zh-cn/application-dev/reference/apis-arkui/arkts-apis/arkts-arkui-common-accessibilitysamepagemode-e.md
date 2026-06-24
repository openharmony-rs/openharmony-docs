# AccessibilitySamePageMode

```TypeScript
declare enum AccessibilitySamePageMode
```

Defines the same page mode

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SEMI_SILENT

```TypeScript
SEMI_SILENT = 0
```

the first page and root page event is not send.but if application load new page whith navigation,the page event will be sent.
this mode is to solve skipping focus

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**卡片能力：** 该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## FULL_SILENT

```TypeScript
FULL_SILENT = 1
```

the all page event is not send

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 该接口支持在原子化服务API中使用。

**卡片能力：** 该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

