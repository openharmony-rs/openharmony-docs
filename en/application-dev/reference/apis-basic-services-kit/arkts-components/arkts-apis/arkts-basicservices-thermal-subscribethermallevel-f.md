# subscribeThermalLevel

## Modules to Import

```TypeScript
import { thermal } from '@kit.BasicServicesKit';
```

## subscribeThermalLevel

```TypeScript
function subscribeThermalLevel(callback: AsyncCallback<ThermalLevel>): void
```

Subscribes to the thermal level changes. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [registerThermalLevelCallback](arkts-basicservices-thermal-registerthermallevelcallback-f.md)

**System capability:** SystemCapability.PowerManager.ThermalManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](arkts-basicservices-base-asynccallback-i.md)&lt;[ThermalLevel](arkts-basicservices-thermal-thermallevel-e.md)&gt; | Yes | Callback used to return thermal level. This parameter is of the function type. |

**Examples**

```TypeScript
thermal.subscribeThermalLevel((err: Error, level: thermal.ThermalLevel) => {
    console.info('thermal level is: ' + level);
});
```
