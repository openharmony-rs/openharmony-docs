# OperationValueType

```TypeScript
export type OperationValueType = number | number | string | boolean
```

表示不同谓词所需要匹配的值。

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

| 类型 | 说明 |
| --- | --- |
| long | 表示字段类型为数字，可取长整型。 |
| double | 表示字段类型为数字，可取小数。 |
| string | 表示字段类型为字符串，可取任意值。 |
| boolean | 表示字段类型为布尔值。 |
