# ErrorCallback

Defines a common callback that carries an error parameter. It is used to return error information when an asynchronous operation fails. The specific error code is defined by each API. For details, please refer to the error code description of the corresponding API.

The information returned by the callback is an error parameter of the [BusinessError](arkts-basicservices-base-businesserror-i.md) type.

@typedef ErrorCallback [since 6 - 10] @typedef ErrorCallback&lt;T extends Error = BusinessError&gt; [since 11]

**Since:** 6

**System capability:** SystemCapability.Base

## Modules to Import

```TypeScript
import { AsyncCallback, BusinessError, Callback, ErrorCallback } from '@kit.BasicServicesKit';
```

## [[Call]]

```TypeScript
(err: T): void
```

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Base

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| err | T | Yes | Common error information returned when the API call fails. The default type is **BusinessError**, including the error code (**code**) and optional additional data (**data**). |
