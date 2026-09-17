# HyperSnapErrorInfo

Describes the Hyper Snap error information.

**Since:** 26.1.0

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## Modules to Import

```TypeScript
import { hyperSnapManager } from '@kit.AbilityKit';
```

## code

```TypeScript
code: HyperSnapErrorCode
```

The error code.

**Type:** [HyperSnapErrorCode](arkts-ability-hypersnapmanager-hypersnaperrorcode-e.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## msg

```TypeScript
msg: string
```

The error message.

**Type:** string

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

## occurTimeStamp

```TypeScript
occurTimeStamp: number
```

The time elapsed from the Unix epoch to the moment the error occurred. Unit: milliseconds. The value should be an integer.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core
