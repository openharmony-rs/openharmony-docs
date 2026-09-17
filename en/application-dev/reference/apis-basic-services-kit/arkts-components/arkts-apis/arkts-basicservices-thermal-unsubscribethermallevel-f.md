# unsubscribeThermalLevel

## Modules to Import

```TypeScript
import { thermal } from '@kit.BasicServicesKit';
```

## unsubscribeThermalLevel

```TypeScript
function unsubscribeThermalLevel(callback?: AsyncCallback<void>): void
```

Unsubscribes from the thermal level changes. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [unregisterThermalLevelCallback](arkts-basicservices-thermal-unregisterthermallevelcallback-f.md)

**System capability:** SystemCapability.PowerManager.ThermalManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | No | Callback that returns no value. If this parameter is not set, all callbacks will be unregistered. |

**Examples**

```TypeScript
thermal.unsubscribeThermalLevel(() => {
    console.info('unsubscribe thermal level success.');
});
```
