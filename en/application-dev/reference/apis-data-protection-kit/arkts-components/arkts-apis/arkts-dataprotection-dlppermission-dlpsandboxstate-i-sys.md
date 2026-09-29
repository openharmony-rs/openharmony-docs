# DLPSandboxState (System API)

```TypeScript
export interface DLPSandboxState
```

Represents the DLP sandbox state information.

**Since:** 10

<!--Device-dlpPermission-export interface DLPSandboxState--><!--Device-dlpPermission-export interface DLPSandboxState-End-->

**System capability:** SystemCapability.Security.DataLossPrevention

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { dlpPermission } from '@kit.DataProtectionKit';
```

## appIndex

```TypeScript
appIndex: number
```

Index of the DLP sandbox application. The value range is [1000, 1100]. If the value is out of range, an error log is generated.

**Type:** number

**Since:** 10

<!--Device-DLPSandboxState-appIndex: number--><!--Device-DLPSandboxState-appIndex: number-End-->

**System capability:** SystemCapability.Security.DataLossPrevention

**System API:** This is a system API.

## bundleName

```TypeScript
bundleName: string
```

Bundle name of the application.

**Type:** string

**Since:** 10

<!--Device-DLPSandboxState-bundleName: string--><!--Device-DLPSandboxState-bundleName: string-End-->

**System capability:** SystemCapability.Security.DataLossPrevention

**System API:** This is a system API.
