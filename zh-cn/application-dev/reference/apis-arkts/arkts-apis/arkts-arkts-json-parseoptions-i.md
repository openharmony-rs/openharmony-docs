# ParseOptions

解析的选项，可定义处理BigInt的模式。

**起始版本：** 12

<!--Device-json-interface ParseOptions--><!--Device-json-interface ParseOptions-End-->

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

**类型：** BigIntMode

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ParseOptions-bigIntMode: BigIntMode--><!--Device-ParseOptions-bigIntMode: BigIntMode-End-->

**系统能力：** SystemCapability.Utils.Lang

