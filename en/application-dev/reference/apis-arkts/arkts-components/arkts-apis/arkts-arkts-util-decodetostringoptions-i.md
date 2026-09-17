# DecodeToStringOptions

Describes the behavioral parameters for the **decodeToString** method when decoding byte streams.

**Since:** 12

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { util } from '@kit.ArkTS';
```

## stream

```TypeScript
stream?: boolean
```

Whether the incomplete byte sequence at the end of the input needs to be appended to the parameter for the next call of **decodeToString**. The value **true** means that the incomplete byte sequence is stored in the internal buffer until the function is called next time. If the value is false, the byte sequence is directly decoded when the function is called currently. The default value is **false**.

**Type:** boolean

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang
