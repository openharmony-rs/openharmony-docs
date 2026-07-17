# RequestResult

模态弹框请求结果，包含结果码ResultCode和请求结果ResultWant。

**起始版本：** 9

<!--Device-dialogRequest-export interface RequestResult--><!--Device-dialogRequest-export interface RequestResult-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## 导入模块

```TypeScript
import { dialogRequest } from '@kit.AbilityKit';
```

## result

```TypeScript
result: ResultCode
```

表示结果码。

**类型：** ResultCode

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RequestResult-result: ResultCode--><!--Device-RequestResult-result: ResultCode-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

## want

```TypeScript
want?: Want
```

表示Want类型信息，如ability名称，包名等。

**类型：** Want

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RequestResult-want?: Want--><!--Device-RequestResult-want?: Want-End-->

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

