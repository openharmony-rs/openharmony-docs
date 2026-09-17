# isStandby

## Modules to Import

```TypeScript
import { power } from '@kit.BasicServicesKit';
```

## isStandby

```TypeScript
function isStandby(): boolean
```

Checks whether the device is in standby mode.

**Since:** 10

**System capability:** SystemCapability.PowerManager.PowerManager.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | The value **true** indicates that the device is in standby mode, and the value **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [4900101](../errorcode-power.md#4900101-service-connection-failure) | Failed to connect to the service. |

**Examples**

```TypeScript
try {
    let isStandby = power.isStandby();
    console.info('device is in standby: ' + isStandby);
} catch(err) {
    console.error('check isStandby failed, err: ' + err);
}
```
