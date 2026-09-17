# UnhandledRejectionObserver

```TypeScript
export type UnhandledRejectionObserver = (reason: Error | any, promise: Promise<any>) => void
```

Defines an observer to capture the cause of a rejected promise.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| reason | Error &#124; any | Yes | Generally, the value is of the **Error** type, indicating the reason for rejection. |
| promise | Promise&lt;any&gt; | Yes | Rejected promise. |
