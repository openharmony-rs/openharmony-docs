# getLevel

## Modules to Import

```TypeScript
import { systemLoad } from '@kit.BasicServicesKit';
```

## getLevel

```TypeScript
function getLevel(): Promise<SystemLoadLevel>
```

Obtains the system load level. This API uses a promise to return the result.

**Since:** 12

**System capability:** SystemCapability.ResourceSchedule.SystemLoad

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[SystemLoadLevel](arkts-basicservices-systemload-systemloadlevel-e.md)&gt; | Promise used to return the system load level. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { systemLoad } from '@kit.BasicServicesKit';

systemLoad.getLevel().then((res: systemLoad.SystemLoadLevel) => {
    console.info(`getLevel promise succeeded. result: ` + JSON.stringify(res));
}).catch((err: BusinessError) => {
    console.error(`getLevel promise failed. code is ${err.code} message is ${err.message}`);
})
```
