# HuksResult

```TypeScript
export interface HuksResult
```

Represents the result returned.

> **NOTE:** 
> 
> - For details about the error codes, see [HUKS Error Codes](../../../reference/apis-universal-keystore-kit/errorcode-huks.md).

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [HuksReturnResult](arkts-universalkeystore-huks-huksreturnresult-i.md)

<!--Device-huks-export interface HuksResult--><!--Device-huks-export interface HuksResult-End-->

**System capability:** SystemCapability.Security.Huks.Extension

## Modules to Import

```TypeScript
import { huks } from '@kit.UniversalKeystoreKit';
```

## certChains

```TypeScript
certChains?: Array<string>
```

Reserved field.

Note: This API is deprecated since API version 9. No substitute API is provided.

**Type:** Array&lt;string&gt;

**Since:** 8

**Deprecated since:** 9

<!--Device-HuksResult-certChains?: Array<string>--><!--Device-HuksResult-certChains?: Array<string>-End-->

**System capability:** SystemCapability.Security.Huks.Extension

## errorCode

```TypeScript
errorCode: number
```

Reserved field.

Note: This API is deprecated since API version 9. No substitute API is provided.

**Type:** number

**Since:** 8

**Deprecated since:** 9

<!--Device-HuksResult-errorCode: number--><!--Device-HuksResult-errorCode: number-End-->

**System capability:** SystemCapability.Security.Huks.Extension

## outData

```TypeScript
outData?: Uint8Array
```

Reserved field.

Note: This API is deprecated since API version 9. No substitute API is provided.

**Type:** Uint8Array

**Since:** 8

**Deprecated since:** 9

<!--Device-HuksResult-outData?: Uint8Array--><!--Device-HuksResult-outData?: Uint8Array-End-->

**System capability:** SystemCapability.Security.Huks.Extension

## properties

```TypeScript
properties?: Array<HuksParam>
```

Reserved field.

Note: This API is deprecated since API version 9. No substitute API is provided.

**Type:** Array&lt;[HuksParam](arkts-universalkeystore-huks-huksparam-i.md)&gt;

**Since:** 8

**Deprecated since:** 9

<!--Device-HuksResult-properties?: Array<HuksParam>--><!--Device-HuksResult-properties?: Array<HuksParam>-End-->

**System capability:** SystemCapability.Security.Huks.Extension
