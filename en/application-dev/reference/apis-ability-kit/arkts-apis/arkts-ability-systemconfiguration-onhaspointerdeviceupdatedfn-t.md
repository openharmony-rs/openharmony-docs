# OnHasPointerDeviceUpdatedFn

```TypeScript
type OnHasPointerDeviceUpdatedFn = (hasPointerDevice: boolean) => void
```

Defines an OnHasPointerDeviceUpdatedFn function.

@typedef { function }

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 24.

<!--Device-systemConfiguration-type OnHasPointerDeviceUpdatedFn = (hasPointerDevice: boolean) => void--><!--Device-systemConfiguration-type OnHasPointerDeviceUpdatedFn = (hasPointerDevice: boolean) => void-End-->

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| hasPointerDevice | boolean | Yes | Indicates whether a pointing device is connected, such as a mouse, keyboard, or touchpad |
