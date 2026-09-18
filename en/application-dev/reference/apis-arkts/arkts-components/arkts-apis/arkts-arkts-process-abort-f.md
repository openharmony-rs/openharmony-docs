# abort

## Modules to Import

```TypeScript
import { process } from '@kit.ArkTS';
```

## abort

```TypeScript
function abort(): void
```

Aborts a process and generates a core file. This method will cause a process to exit immediately. Exercise caution when using this method.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Utils.Lang

**Examples**

```TypeScript
process.abort();
```
