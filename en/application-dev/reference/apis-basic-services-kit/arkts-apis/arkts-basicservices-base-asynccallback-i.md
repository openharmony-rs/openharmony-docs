# AsyncCallback

Defines a common callback that carries an error parameter and asynchronous return value. It is used to return error information or success data when an asynchronous operation is complete.

The error parameter is of the [BusinessError](arkts-basicservices-base-businesserror-i.md) type.

The type of the asynchronous return value is defined by the developer.

@typedef AsyncCallback [since 6 - 11] @typedef AsyncCallback&lt;T, E = void&gt; [since 12]

**Since:** 6

**System capability:** SystemCapability.Base

## Modules to Import

```TypeScript
import { AsyncCallback, BusinessError, Callback, ErrorCallback } from '@kit.BasicServicesKit';
```

## [[Call]]

```TypeScript
(err: BusinessError<E>, data: T): void
```

**Since:** 6

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

**System capability:** SystemCapability.Base

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| err | [BusinessError](arkts-basicservices-base-businesserror-i.md)&lt;E&gt; | Yes | Common error information returned when the API call fails, including the error code and optional additional data. If the parameter of the **E** type is not specified, the default value **void** is used. In this case, **BusinessError** contains only the error code. If the API call succeeds, this parameter returns **null**. |
| data | T | Yes | Data returned asynchronously when the API is successfully called. The data type is defined by the developer. This parameter is unavailable when the API call fails. |
