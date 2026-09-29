# DataBlob

```TypeScript
interface DataBlob
```

Encapsulates binary data. The core field **data** is of the Uint8Array type.

> **NOTE:** 
> 
> The Uint8Array typed array represents an array of 8-bit unsigned integers.

**Since:** 9

<!--Device-cryptoFramework-interface DataBlob--><!--Device-cryptoFramework-interface DataBlob-End-->

**System capability:** SystemCapability.Security.CryptoFramework

## Modules to Import

```TypeScript
import { cryptoFramework } from '@kit.CryptoArchitectureKit';
```

## data

```TypeScript
data: Uint8Array
```

Binary data array.

**Type:** Uint8Array

**Since:** 9

**Model restriction:** 
- API version 12 and later: This API can be used in both the stage model and FA model.
- API versions 9 to 11: This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-DataBlob-data: Uint8Array--><!--Device-DataBlob-data: Uint8Array-End-->

**System capability:** SystemCapability.Security.CryptoFramework
