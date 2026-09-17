# ReturningConfig

Specifies the list of field names to return after returning-related APIs are called and the maximum number of records allowed in the result set.

**Since:** 23

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## Modules to Import

```TypeScript
import { relationalStore } from '@kit.ArkData';
```

## columns

```TypeScript
columns: Array<string>
```

Fields returned in the result set. One to four fields are supported for input. Note: Field names containing spaces ( ), commas (,), or asterisks (*) are not allowed.

**Type:** Array&lt;string&gt;

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## maxReturningCount

```TypeScript
maxReturningCount?: number
```

Maximum number of rows returned in the result set. The default value is **1024**, and the maximum value is **32766**. Note: If the actual number of modified rows exceeds the value set for **maxReturningCount**, the system will discard the excess data.

**Type:** number

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core
