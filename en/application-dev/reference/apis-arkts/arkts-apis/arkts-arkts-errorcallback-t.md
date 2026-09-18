# ErrorCallback

```TypeScript
type ErrorCallback = (err: ErrorEvent) => void
```

The event handler to be called when an exception occurs during worker execution.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| err | [ErrorEvent](arkts-arkts-worker-errorevent-i.md) | Yes | Error event class, which provides detailed information about the exception occurred during Worker execution. |
