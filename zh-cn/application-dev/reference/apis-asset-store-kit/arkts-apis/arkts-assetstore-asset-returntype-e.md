# ReturnType

枚举，关键资产查询返回的结果类型。

**起始版本：** 11

<!--Device-asset-enum ReturnType--><!--Device-asset-enum ReturnType-End-->

**系统能力：** SystemCapability.Security.Asset

## ALL

```TypeScript
ALL = 0
```

返回关键资产明文及属性。

**说明：** 查询单条关键资产明文时，需设置此类型。

**起始版本：** 11

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-ReturnType-ALL = 0--><!--Device-ReturnType-ALL = 0-End-->

**系统能力：** SystemCapability.Security.Asset

## ATTRIBUTES

```TypeScript
ATTRIBUTES = 1
```

返回关键资产属性，不含关键资产明文。

**说明：** 批量查询关键资产属性时，需设置此类型。

**起始版本：** 11

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-ReturnType-ATTRIBUTES = 1--><!--Device-ReturnType-ATTRIBUTES = 1-End-->

**系统能力：** SystemCapability.Security.Asset

