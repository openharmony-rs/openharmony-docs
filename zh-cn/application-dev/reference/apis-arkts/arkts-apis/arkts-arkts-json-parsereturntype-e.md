# ParseReturnType

```TypeScript
const enum ParseReturnType
```

枚举解析返回结果的类型。

当parseReturnType为MAP时，解析结果为collection.Map而非Sendable对象。仅对[parseSendable](arkts-arkts-json-parsesendable-f.md)生效；[parse](arkts-arkts-json-parse-f.md)会忽略该字段。

**起始版本：** 26.0.1

<!--Device-json-const enum ParseReturnType--><!--Device-json-const enum ParseReturnType-End-->

**系统能力：** SystemCapability.Utils.Lang

## MAP

```TypeScript
MAP = 1
```

解析结果为collections.Map，支持任意条数的增删操作。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-ParseReturnType-MAP = 1--><!--Device-ParseReturnType-MAP = 1-End-->

**系统能力：** SystemCapability.Utils.Lang

## OBJECT

```TypeScript
OBJECT = 0
```

解析结果为不可扩展的Sendable对象，其已有属性可更新、不可新增或删除。

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

<!--Device-ParseReturnType-OBJECT = 0--><!--Device-ParseReturnType-OBJECT = 0-End-->

**系统能力：** SystemCapability.Utils.Lang
