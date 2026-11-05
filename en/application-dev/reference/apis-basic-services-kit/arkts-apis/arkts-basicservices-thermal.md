# @ohos.thermal(Thermal Management)

The **thermal** module provides thermal level-related callback and query APIs to obtain the information required for thermal control.

**Since:** 8

<!--Device-unnamed-declare namespace thermal--><!--Device-unnamed-declare namespace thermal-End-->

**System capability:** SystemCapability.PowerManager.ThermalManager

## Modules to Import

```TypeScript
import { thermal } from '@kit.BasicServicesKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getLevel](arkts-basicservices-thermal-getlevel-f.md#getlevel-1) | Obtains the current thermal level. |
| [registerThermalLevelCallback](arkts-basicservices-thermal-registerthermallevelcallback-f.md#registerthermallevelcallback-1) | Subscribe to the callback notification when the hot level changes. Use callback asynchronous callback. When the device temperature exceeds the threshold and the heat level changes, the system automatically triggers a callback notification and returns the changed heat level through the callback. This method is used in conjunction with [thermal.unregisterThermalLevelCallback](arkts-basicservices-thermal-unregisterthermallevelcallback-f.md), Used to cancel a previously registered hot gear callback. |
| [unregisterThermalLevelCallback](arkts-basicservices-thermal-unregisterthermallevelcallback-f.md#unregisterthermallevelcallback-1) | Unsubscribe from the callback notification when the hot level changes. Use callback asynchronous callback. This method is used in conjunction with thermal.registerThermalLevelCallback, Used to cancel a previously registered hot gear callback. No error is reported when unsubscribing from an unregistered callback, and no operation is performed. |
| [getThermalLevel](arkts-basicservices-thermal-getthermallevel-f.md#getthermallevel-1) | Obtains the current thermal level. |
| [subscribeThermalLevel](arkts-basicservices-thermal-subscribethermallevel-f.md#subscribethermallevel-1) | Subscribes to the thermal level changes. This API uses an asynchronous callback to return the result. |
| [unsubscribeThermalLevel](arkts-basicservices-thermal-unsubscribethermallevel-f.md#unsubscribethermallevel-1) | Unsubscribes from the thermal level changes. This API uses an asynchronous callback to return the result. |

### Enums

| Name | Description |
| --- | --- |
| [ThermalLevel](arkts-basicservices-thermal-thermallevel-e.md) | Enumerates thermal levels. |
