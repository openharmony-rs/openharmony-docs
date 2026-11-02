# PinComplexityPolicy (System API)

```TypeScript
interface PinComplexityPolicy
```

PIN complexity check policy and description.

**Since:** 26.1.0

<!--Device-pinAuth-interface PinComplexityPolicy--><!--Device-pinAuth-interface PinComplexityPolicy-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { pinAuth } from '@kit.UserAuthenticationKit';
```

## complexityReg

```TypeScript
complexityReg: string
```

Regular expression for PIN complexity check.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-PinComplexityPolicy-complexityReg: string--><!--Device-PinComplexityPolicy-complexityReg: string-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**System API:** This is a system API.

## policyDescription

```TypeScript
policyDescription: string
```

Description of the PIN complexity policy.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-PinComplexityPolicy-policyDescription: string--><!--Device-PinComplexityPolicy-policyDescription: string-End-->

**System capability:** SystemCapability.UserIAM.UserAuth.Core

**System API:** This is a system API.
