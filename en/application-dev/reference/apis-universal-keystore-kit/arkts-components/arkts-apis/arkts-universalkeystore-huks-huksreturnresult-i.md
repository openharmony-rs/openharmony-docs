# HuksReturnResult

Represents the result returned.

**Since:** 9

**System capability:** SystemCapability.Security.Huks.Core

## Modules to Import

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
```

## certChains

```TypeScript
certChains?: Array<string>
```

Certificate chain information. The default value is **undefined**.

**Type:** Array&lt;string&gt;

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Security.Huks.Core

## outData

```TypeScript
outData?: Uint8Array
```

Challenge obtained after the [initSession](arkts-universalkeystore-huks-initsession-f.md) operation. The default value is **undefined**.

**Type:** Uint8Array

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Security.Huks.Core

## properties

```TypeScript
properties?: Array<HuksParam>
```

Challenge obtained after the [initSession](arkts-universalkeystore-huks-initsession-f.md) operation. The default value is **undefined**.

**Type:** Array&lt;[HuksParam](arkts-universalkeystore-huks-huksparam-i.md)&gt;

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Security.Huks.Core

## sharedSecret

```TypeScript
sharedSecret?: Uint8Array
```

Shared key.

**Type:** Uint8Array

**Since:** 26.0.0

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Security.Huks.Core
