# ErrorHandler

```TypeScript
export type ErrorHandler = (errObject: Error) => void
```

The ErrorHandler will be called when the ArkTS runtime throws an exception that is not caught by the user.

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| errObject | Error | Yes | Event name, message, and error stack of the exception. |
