# @ohos.thermal(Thermal Management)

The **thermal** module provides thermal level-related callback and query APIs to obtain the information required for thermal control.

**Since:** 8

**System capability:** SystemCapability.PowerManager.ThermalManager

## Modules to Import

```TypeScript
import { thermal } from '@kit.BasicServicesKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getLevel](arkts-basicservices-thermal-getlevel-f.md) | Obtains the current thermal level. |
| [getThermalLevel](arkts-basicservices-thermal-getthermallevel-f.md) | Obtains the current thermal level. |
| [registerThermalLevelCallback](arkts-basicservices-thermal-registerthermallevelcallback-f.md) | Registers a callback to be invoked when the thermal level changes. This API uses an asynchronous callback to return the result. |
| [subscribeThermalLevel](arkts-basicservices-thermal-subscribethermallevel-f.md) | Subscribes to the thermal level changes. This API uses an asynchronous callback to return the result. |
| [unregisterThermalLevelCallback](arkts-basicservices-thermal-unregisterthermallevelcallback-f.md) | Unregisters from the thermal level changes. This API uses an asynchronous callback to return the result. |
| [unsubscribeThermalLevel](arkts-basicservices-thermal-unsubscribethermallevel-f.md) | Unsubscribes from the thermal level changes. This API uses an asynchronous callback to return the result. |

### Enums

| Name | Description |
| --- | --- |
| [ThermalLevel](arkts-basicservices-thermal-thermallevel-e.md) | Enumerates thermal levels. |
