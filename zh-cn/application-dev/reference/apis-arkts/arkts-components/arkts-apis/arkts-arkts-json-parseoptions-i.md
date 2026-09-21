# ParseOptions

```TypeScript
interface ParseOptions
```

解析的选项，可定义处理BigInt的模式。

**起始版本：** 12

**系统能力：** SystemCapability.Utils.Lang

## 导入模块

```TypeScript
import { JSON } from '@kit.ArkTS';
```

## bigIntMode

```TypeScript
bigIntMode: BigIntMode
```

定义处理BigInt的模式。由于JSON规范不支持BigInt类型，且Number精度范围为-(2^53-1)到(2^53-1)，本模块提供三种模式以适配不同场景的整数精度需求。

**类型：** [BigIntMode](arkts-arkts-json-bigintmode-e.md)

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang

## parseReturnType

```TypeScript
parseReturnType?: ParseReturnType
```

解析返回结果的类型。省略时默认为OBJECT。仅对[parseSendable](arkts-arkts-json-parsesendable-f.md)生效；[parse](arkts-arkts-json-parse-f.md)会忽略该字段。

**类型：** [ParseReturnType](arkts-arkts-json-parsereturntype-e.md)

**起始版本：** 26.0.1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.1开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Utils.Lang
