# DLPSandboxInfo (System API)

```TypeScript
export interface DLPSandboxInfo
```

Represents the DLP sandbox information.

**Since:** 10

<!--Device-dlpPermission-export interface DLPSandboxInfo--><!--Device-dlpPermission-export interface DLPSandboxInfo-End-->

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

Index of the DLP sandbox application.

**Type:** number

**Since:** 10

<!--Device-DLPSandboxInfo-appIndex: number--><!--Device-DLPSandboxInfo-appIndex: number-End-->

**System capability:** SystemCapability.Security.DataLossPrevention

**System API:** This is a system API.

## bindAppIndex

```TypeScript
bindAppIndex?: number
```

Index of the DLP sandbox application to be bound. This parameter is not returned by default. It is returned only when the sandbox application is Preview.

**Type:** number

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-DLPSandboxInfo-bindAppIndex?: number--><!--Device-DLPSandboxInfo-bindAppIndex?: number-End-->

**System capability:** SystemCapability.Security.DataLossPrevention

**System API:** This is a system API.

## tokenID

```TypeScript
tokenID: number
```

Token ID of the DLP sandbox application.

**Type:** number

**Since:** 10

<!--Device-DLPSandboxInfo-tokenID: number--><!--Device-DLPSandboxInfo-tokenID: number-End-->

**System capability:** SystemCapability.Security.DataLossPrevention

**System API:** This is a system API.
