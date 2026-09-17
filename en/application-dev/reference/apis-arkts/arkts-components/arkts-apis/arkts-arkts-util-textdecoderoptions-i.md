# TextDecoderOptions

Describes decoding-related options, which include **fatal** and **ignoreBOM**.

**Since:** 11

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { util } from '@kit.ArkTS';
```

## fatal

```TypeScript
fatal?: boolean
```

Whether to display fatal errors. The value **true** means to display fatal errors, and **false** means the opposite. The default value is **false**.

**Type:** boolean

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

## ignoreBOM

```TypeScript
ignoreBOM?: boolean
```

Whether to ignore the BOM. The value **true** means to ignore the BOM, and **false** means the opposite. The default value is **false**.

**Type:** boolean

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang
