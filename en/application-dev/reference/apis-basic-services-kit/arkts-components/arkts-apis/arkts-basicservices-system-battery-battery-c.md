# Battery

The module allows you to query the charging status and remaining power of a device.

**Since:** 3

**Deprecated since:** 6

**System capability:** SystemCapability.PowerManager.BatteryManager.Lite

## Modules to Import

```TypeScript
import { Battery, BatteryResponse, GetStatusOptions } from '@kit.BasicServicesKit';
```

## getStatus

```TypeScript
static getStatus(options?: GetStatusOptions): void
```

Obtains the current charging state and battery level.

**Since:** 3

**Deprecated since:** 6

**System capability:** SystemCapability.PowerManager.BatteryManager.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [GetStatusOptions](arkts-basicservices-system-battery-getstatusoptions-i.md) | No | Object that contains the API calling result. This parameter is optional and is left blank by default. |

**Examples**

```TypeScript
ArkTS example:
```

```TypeScript
JS example:
```

```TypeScript
/* xxx.css */
.container {
  width: 100%;
  height: 100%;
  justify-content: center;
  align-items: center;
  flex-direction: column;
}
.title {
  width: 200px;
  font-size: 30px;
  text-align: center;
}
```

```TypeScript
// xxx.js
import Battery from '@system.battery';

export default {
    data: {
        capacity: '',
        charging: ''
    },
    getBatteryInfo() {
        let TAG = 'get_status_success_test';
        Battery.getStatus({
            success: (batteryResponse) => {
                this.capacity = batteryResponse.level;
                this.charging = batteryResponse.charging;
                console.info(`${TAG} batteryResponse.level: ${batteryResponse.level}`);
                console.info(`${TAG} batteryResponse.charging: ${batteryResponse.charging}`);
            },
            fail: (data, code) => {
                console.error(`${TAG} fail data: ${data}, code: ${code}`);
            },
            complete: () => {
                console.info(`${TAG} getStatus complete`);
            }
        });
    },
}
```
