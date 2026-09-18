# AutoFinalizerCleaner

A cleaner for releasing resources managed by developers through a developer-defined callback.

**Since:** 22

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { util } from '@kit.ArkTS';
```

## register

```TypeScript
static register<T>(obj: AutoFinalizer<T>, heldValue: T): void
```

Register objects that release resources managed by developers.

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| obj | [AutoFinalizer](arkts-arkts-util-autofinalizer-i.md)&lt;T&gt; | Yes | The object is registered to the cleaner. |
| heldValue | T | Yes | The value to pass to the finalizer. |
