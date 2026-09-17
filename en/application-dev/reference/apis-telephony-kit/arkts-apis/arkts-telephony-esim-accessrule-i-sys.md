# AccessRule (System API)

Establishes a single UICC access rule pursuant to the GlobalPlatform Secure Element Access Control specification.

@interface AccessRule

**Since:** 20

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { eSIM } from '@kit.TelephonyKit';
```

## accessType

```TypeScript
accessType: number
```

The type of access.

**Type:** number

**Since:** 20

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.

## certificateHashHexStr

```TypeScript
certificateHashHexStr: string
```

Certificate hash hexadecimal string.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.

## packageName

```TypeScript
packageName: string
```

The name of package.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.Telephony.CoreService.Esim

**System API:** This is a system API.
