# ErrorHandler

```TypeScript
export type ErrorHandler = (errObject: Error) => void
```

The ErrorHandler will be called when the ArkTS runtime throws an exception that is not caught by the user.

**Since:** 21

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 21.

<!--Device-errorManager-export type ErrorHandler = (errObject: Error) => void--><!--Device-errorManager-export type ErrorHandler = (errObject: Error) => void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| errObject | Error | Yes | Event name, message, and error stack of the exception. |
