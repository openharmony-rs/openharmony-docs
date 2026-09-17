# DecodeWithStreamOptions

Defines whether decoding follows data blocks.

**Since:** 11

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { util } from '@kit.ArkTS';
```

## stream

```TypeScript
stream?: boolean
```

Whether to allow data blocks in subsequent **decodeWithStream()**. If data is processed in blocks, set this parameter to **true**. If this is the last data block to process or data is not divided into blocks, set this parameter to **false**. The default value is **false**.

**Type:** boolean

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang
