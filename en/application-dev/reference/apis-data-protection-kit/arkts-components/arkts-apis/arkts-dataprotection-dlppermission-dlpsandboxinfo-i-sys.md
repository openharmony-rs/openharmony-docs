# DLPSandboxInfo (System API)

Represents the DLP sandbox information.

**Since:** 10

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

**System capability:** SystemCapability.Security.DataLossPrevention

**System API:** This is a system API.

## tokenID

```TypeScript
tokenID: number
```

Token ID of the DLP sandbox application.

**Type:** number

**Since:** 10

**System capability:** SystemCapability.Security.DataLossPrevention

**System API:** This is a system API.
