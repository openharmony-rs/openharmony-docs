# RotationChangeCallback

```TypeScript
type RotationChangeCallback<T, U> = (info: T) => U
```

Describes a generic callback function for rotation event notifications.

In this callback function, the parameter type is [RotationChangeInfo](arkts-arkui-window-rotationchangeinfo-i.md), and the return value type is [RotationChangeResult](arkts-arkui-window-rotationchangeresult-i.md) \| void.

**Since:** 19

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| info | T | Yes | Parameter of type [RotationChangeInfo](arkts-arkui-window-rotationchangeinfo-i.md) passed by the system when the callback function is called. |

**Return value:**

| Type | Description |
| --- | --- |
| U | Value of type [RotationChangeResult](arkts-arkui-window-rotationchangeresult-i.md) &#124; void. |
