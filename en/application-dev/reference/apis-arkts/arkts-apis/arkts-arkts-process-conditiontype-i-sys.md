# ConditionType (System API)

Provides the ConditionType type,including timeout, killSignal, maxBuffer.

**Since:** 10

**System capability:** SystemCapability.Utils.Lang

**System API:** This is a system API.

**Test API:** This API is used only in automated test scripts.

## Modules to Import

```TypeScript
import { process } from '@kit.ArkTS';
```

## killSignal

```TypeScript
killSignal?: number | string
```

Signal sent to the child process when the running time of a child process exceeds the timeout period.

**Type:** number &#124; string

**Since:** 10

**System capability:** SystemCapability.Utils.Lang

**System API:** This is a system API.

**Test API:** This API is used only in automated test scripts.

## maxBuffer

```TypeScript
maxBuffer?: number
```

Maximum buffer size for the standard input and output of the child process.

**Type:** number

**Since:** 10

**System capability:** SystemCapability.Utils.Lang

**System API:** This is a system API.

**Test API:** This API is used only in automated test scripts.

## timeout

```TypeScript
timeout?: number
```

Maximum running time (in ms) of the child process.

**Type:** number

**Since:** 10

**System capability:** SystemCapability.Utils.Lang

**System API:** This is a system API.

**Test API:** This API is used only in automated test scripts.
