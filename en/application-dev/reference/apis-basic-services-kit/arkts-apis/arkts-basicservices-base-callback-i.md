# Callback

Defines a common callback used to return the processing result when an asynchronous operation is successful. You need to define the callback type.

@typedef { Callback } [since 6 - 11] @typedef { Callback&lt;T&gt; } [since 12]

**Since:** 6

**System capability:** SystemCapability.Base

## Modules to Import

```TypeScript
import { AsyncCallback, BusinessError, Callback, ErrorCallback } from '@kit.BasicServicesKit';
```

## [[Call]]

```TypeScript
(data: T): void
```

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Base

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | T | Yes | Common callback information. You need to define the callback type. The callback is used to return data of the corresponding type. No data is returned if the callback fails. |
