# registerThermalLevelCallback

## Modules to Import

```TypeScript
import { thermal } from '@kit.BasicServicesKit';
```

## registerThermalLevelCallback

```TypeScript
function registerThermalLevelCallback(callback: Callback<ThermalLevel>): void
```

Subscribe to the callback notification when the hot level changes. Use callback asynchronous callback. When the device temperature exceeds the threshold and the heat level changes, the system automatically triggers a callback notification and returns the changed heat level through the callback. This method is used in conjunction with [thermal.unregisterThermalLevelCallback](arkts-basicservices-thermal-unregisterthermallevelcallback-f.md), Used to cancel a previously registered hot gear callback.

- Only one callback is supported per process, and repeated subscriptions will be overwritten.  
- The callback function must be returned as soon as possible. Do not perform time-consuming operations(such as  
synchronizing file I/Os). Otherwise, the delivery of system hot-level notifications may be blocked.  
- When the hot management service restarts abnormally, the registered callback will automatically become invalid  
and no notification will be received. The developer needs to call registerThermalLevelCallback again to resume the subscription.  
- Subscriptions may fail silently without throwing an exception when the hot management service is unavailable.  
Developers cannot determine whether the subscription is successful based on the returned value. It is recommended to verify service availability via [thermal.getLevel](arkts-basicservices-thermal-getlevel-f.md) after subscription (If the [thermal.getLevel](arkts-basicservices-thermal-getlevel-f.md) returns COOL and the device is significantly hot, the service may not be available).

**Since:** 9

<!--Device-thermal-function registerThermalLevelCallback(callback: Callback<ThermalLevel>): void--><!--Device-thermal-function registerThermalLevelCallback(callback: Callback<ThermalLevel>): void-End-->

**System capability:** SystemCapability.PowerManager.ThermalManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;[ThermalLevel](arkts-basicservices-thermal-thermallevel-e.md)&gt; | Yes | Callback used to return thermal level. This parameter is of the function type. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Examples**

```TypeScript
try {
    thermal.registerThermalLevelCallback((level: thermal.ThermalLevel) => {
        console.info('thermal level is: ' + level);
    });
    console.info('register thermal level callback success.');
} catch(err) {
    console.error('register thermal level callback failed, err: ' + err);
}
```
