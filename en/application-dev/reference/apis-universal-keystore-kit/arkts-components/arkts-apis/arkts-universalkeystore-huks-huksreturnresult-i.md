# HuksReturnResult

```TypeScript
export interface HuksReturnResult
```

Represents the result returned.

**Since:** 9

<!--Device-huks-export interface HuksReturnResult--><!--Device-huks-export interface HuksReturnResult-End-->

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

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-HuksReturnResult-certChains?: Array<string>--><!--Device-HuksReturnResult-certChains?: Array<string>-End-->

**System capability:** SystemCapability.Security.Huks.Core

## outData

```TypeScript
outData?: Uint8Array
```

Challenge obtained after the [initSession](arkts-universalkeystore-huks-initsession-f.md) operation. The default value is **undefined**.

**Type:** Uint8Array

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-HuksReturnResult-outData?: Uint8Array--><!--Device-HuksReturnResult-outData?: Uint8Array-End-->

**System capability:** SystemCapability.Security.Huks.Core

## properties

```TypeScript
properties?: Array<HuksParam>
```

Challenge obtained after the [initSession](arkts-universalkeystore-huks-initsession-f.md) operation. The default value is **undefined**.

**Type:** Array&lt;[HuksParam](arkts-universalkeystore-huks-huksparam-i.md)&gt;

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-HuksReturnResult-properties?: Array<HuksParam>--><!--Device-HuksReturnResult-properties?: Array<HuksParam>-End-->

**System capability:** SystemCapability.Security.Huks.Core

## sharedSecret

```TypeScript
sharedSecret?: Uint8Array
```

Shared key.

**Type:** Uint8Array

**Since:** 26.0.0

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-HuksReturnResult-sharedSecret?: Uint8Array--><!--Device-HuksReturnResult-sharedSecret?: Uint8Array-End-->

**System capability:** SystemCapability.Security.Huks.Core
