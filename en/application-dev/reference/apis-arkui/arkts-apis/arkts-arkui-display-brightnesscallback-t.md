# BrightnessCallback

```TypeScript
type BrightnessCallback<T1, T2> = (data1: T1, data2: T2) => void
```

Defines the callback function used to listen for screen brightness information.

**Since:** 22

**System capability:** SystemCapability.Window.SessionManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data1 | T1 | Yes | Display ID. The value is of the number type. |
| data2 | T2 | Yes | Brightness information. The value is of the [BrightnessInfo](arkts-arkui-display-brightnessinfo-i.md) type. |
