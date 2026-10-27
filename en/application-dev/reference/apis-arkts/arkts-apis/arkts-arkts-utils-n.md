# utils(Defines the utils for ArkTS)

```TypeScript
declare namespace utils
```

**Since:** 12

<!--Device-unnamed-declare namespace utils--><!--Device-unnamed-declare namespace utils-End-->

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { ArkTSUtils } from '@kit.ArkTS';
```

## Summary

### Namespaces

| Name | Description |
| --- | --- |
| [ASON](arkts-arkts-utils-ason-n.md) | ArkTS JSON utils. |
| [locks](arkts-arkts-utils-locks-n.md) | Asynchronous lock. |

### Functions

| Name | Description |
| --- | --- |
| [isSendable](arkts-arkts-utils-issendable-f.md#issendable-1) | Checks whether an ArkTS value is sendable. |

### Classes

| Name | Description |
| --- | --- |
| [Atomics](arkts-arkts-utils-atomics-c.md) | Provides atomic operations for ArkTS integer typed arrays backed by an ArkTS ArrayBuffer. Unlike the ECMAScript built-in Atomics object, this class is exposed through the utils module and provides only static methods for ArkTS typed arrays. |
| [SendableLruCache](arkts-arkts-utils-sendablelrucache-c.md) | Object used for store least recently used sendable Object. |
