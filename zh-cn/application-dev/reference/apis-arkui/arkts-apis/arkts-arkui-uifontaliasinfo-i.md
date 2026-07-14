# UIFontAliasInfo

系统的UI字体配置信息。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## name

```TypeScript
name: string
```

别名名称。

**类型：** string

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## weight

```TypeScript
weight: number
```

当weight>0时表示此字体集只包含所指定weight的字体，当weight=0时，表示此字体集包含所有字体。

可返回的值有0、100、400、700、900。

**类型：** number

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

