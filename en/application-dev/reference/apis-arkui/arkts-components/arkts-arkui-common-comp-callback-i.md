# Callback

```TypeScript
declare interface Callback<T, V = void>
```

Defines the basic callback.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## [[Call]]

```TypeScript
(data: T): V
```

Defines the callback info.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | T | Yes | the data will be used in the callback. |

**Return value:**

| Type | Description |
| --- | --- |
| V | Returns result of the callback. |
