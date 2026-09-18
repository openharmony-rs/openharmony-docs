# GlobalObserver

```TypeScript
export type GlobalObserver = (reason: GlobalError) => void
```

Defines an exception observer that can be used as an input parameter for [errorManager.on('globalErrorOccurred')](arkts-ability-errormanager-on-f.md#onglobalerroroccurred) and [errorManager.on('globalUnhandledRejectionDetected')](arkts-ability-errormanager-on-f.md#onglobalunhandledrejectiondetected) to monitor event processing on the main thread of the current application.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| reason | [GlobalError](arkts-ability-errormanager-globalerror-i.md) | Yes | Object related to the exception event name, message, error stack information, exception thread name, and exception thread type. |
