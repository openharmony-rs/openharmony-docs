# Battery

该模块提供充电状态及剩余电量的查询功能。

**起始版本：** 3

**废弃版本：** 6

<!--Device-unnamed-export default class Battery--><!--Device-unnamed-export default class Battery-End-->

**系统能力：** SystemCapability.PowerManager.BatteryManager.Lite

## 导入模块

```TypeScript
import { GetStatusOptions, BatteryResponse } from '@kit.BasicServicesKit';
```

<a id="getstatus"></a>
## getStatus

```TypeScript
static getStatus(options?: GetStatusOptions): void
```

获取设备当前的充电状态及剩余电量。

**起始版本：** 3

**废弃版本：** 6

<!--Device-Battery-static getStatus(options?: GetStatusOptions): void--><!--Device-Battery-static getStatus(options?: GetStatusOptions): void-End-->

**系统能力：** SystemCapability.PowerManager.BatteryManager.Lite

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [GetStatusOptions](arkts-basicservices-battery-getstatusoptions-i.md) | 否 | 包含接口调用结果的对象。可选，默认为空。 |

**示例：**

ArkTS示例：

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

JS示例：

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

