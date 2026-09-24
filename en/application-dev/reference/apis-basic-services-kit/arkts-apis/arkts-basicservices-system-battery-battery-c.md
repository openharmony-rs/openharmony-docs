# Battery

```TypeScript
export default class Battery
```

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

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.PowerManager.BatteryManager.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [GetStatusOptions](arkts-basicservices-system-battery-getstatusoptions-i.md) | No | Object that contains the API calling result. This parameter is optional and is left blank by default. |

**Examples**

ArkTS example:

```TypeScript
Battery.getStatus({
    success: (data: BatteryResponse) => {
        console.info('success get battery level:' + data.level);
    },
    fail: (data: string, code: number) => {
        console.error('fail to get battery level code:' + code + ', data: ' + data);
    }
});
```

JS example:

```TypeScript
<!-- xxx.hml -->
<div class="container">
    <input type="button" value="Get Data" style="width: 240px; height: 50px; margin: 5px;" onclick="getBatteryInfo"></input>
    <text class="title">level: {{ capacity }}</text>
    <text class="title">charging: {{ charging }}</text>
</div>
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
