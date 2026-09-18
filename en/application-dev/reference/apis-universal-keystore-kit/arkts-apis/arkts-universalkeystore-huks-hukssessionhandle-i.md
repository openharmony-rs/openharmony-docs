# HuksSessionHandle

Defines the struct for a HUKS handle.

**Since:** 9

**System capability:** SystemCapability.Security.Huks.Core

## Modules to Import

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
```

## challenge

```TypeScript
challenge?: Uint8Array
```

Challenge obtained after the [initSession](arkts-universalkeystore-huks-initsession-f.md) operation. The default value is **undefined**.

**Type:** Uint8Array

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Security.Huks.Core

## handle

```TypeScript
handle: number
```

Handle of the unsigned integer type.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Security.Huks.Core
