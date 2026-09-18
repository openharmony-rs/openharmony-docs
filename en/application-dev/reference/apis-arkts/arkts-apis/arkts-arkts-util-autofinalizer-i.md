# AutoFinalizer

Provides an interface that can be implemented for releasing a resource which is managed by developers through a developer-defined callback.

**Since:** 22

**System capability:** SystemCapability.Utils.Lang

## Modules to Import

```TypeScript
import { util } from '@kit.ArkTS';
```

## onFinalization

```TypeScript
onFinalization(heldValue: T): void
```

The developer-defined callback used to release resources.

**Since:** 22

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| heldValue | T | Yes | The value to pass to the finalizer. |
