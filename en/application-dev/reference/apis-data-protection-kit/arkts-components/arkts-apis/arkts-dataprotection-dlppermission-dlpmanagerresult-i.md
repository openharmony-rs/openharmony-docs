# DLPManagerResult

```TypeScript
export interface DLPManagerResult
```

Represents information about the trigger of the DLP manager application.

**Since:** 11

**System capability:** SystemCapability.Security.DataLossPrevention

## Modules to Import

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

## resultCode

```TypeScript
resultCode: number
```

Result code returned after the DLP manager application is started and exits. The value ranges from 0 to 3. The value **0** indicates success, while other values indicate failure.

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.DataLossPrevention

## want

```TypeScript
want: Want
```

Data returned after the DLP manager application is started and exits.

**Type:** [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Security.DataLossPrevention
