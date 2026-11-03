# PinComplexityPolicy（系统接口）

```TypeScript
interface PinComplexityPolicy
```

PIN码复杂度检查策略及说明。

**起始版本：** 26.1.0

<!--Device-pinAuth-interface PinComplexityPolicy--><!--Device-pinAuth-interface PinComplexityPolicy-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { pinAuth } from '@kit.UserAuthenticationKit';
```

## complexityReg

```TypeScript
complexityReg: string
```

PIN码复杂度检查正则表达式。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PinComplexityPolicy-complexityReg: string--><!--Device-PinComplexityPolicy-complexityReg: string-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**系统接口：** 此接口为系统接口。

## policyDescription

```TypeScript
policyDescription: string
```

PIN码复杂度策略说明。

**类型：** string

**起始版本：** 26.1.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PinComplexityPolicy-policyDescription: string--><!--Device-PinComplexityPolicy-policyDescription: string-End-->

**系统能力：** SystemCapability.UserIAM.UserAuth.Core

**系统接口：** 此接口为系统接口。
