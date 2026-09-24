# off

## Modules to Import

```TypeScript
import { systemLoad } from '@kit.BasicServicesKit';
```

## off('systemLoadChange')

```TypeScript
function off(type: 'systemLoadChange', callback?: Callback<SystemLoadLevel>): void
```

Disables listening for system load level changes. This API uses an asynchronous callback to return the result.

**Since:** 12

**System capability:** SystemCapability.ResourceSchedule.SystemLoad

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| type | 'systemLoadChange' | Yes | Change type. This parameter has a fixed value of **systemLoadChange**. |
| callback | [Callback](arkts-basicservices-base-callback-i.md)&lt;[SystemLoadLevel](arkts-basicservices-systemload-systemloadlevel-e.md)&gt; | No | Callback used to return the system load level. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible cause: 1. Callback parameter error;<br> 2. Unregister type has not register; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { systemLoad } from '@kit.BasicServicesKit';

function onSystemLoadChange(res: systemLoad.SystemLoadLevel) {
    console.info(`system load changed, current level ` + res);
}

try {
    systemLoad.off('systemLoadChange', onSystemLoadChange);
    console.info(`unregister systemload callback succeeded:. `);
} catch (err) {
    console.error(`unregister systemload callback failed: ` + JSON.stringify(err));
}
```
