# getAltitude

## getAltitude

```TypeScript
function getAltitude(seaPressure: number, currentPressure: number, callback: AsyncCallback<number>): void
```

根据气压值获取设备所在的海拔高度，使用Callback异步方式返回结果。 > **说明**： > > 从API version 8 开始支持，从API version 9 开始废弃，建议使用 > [sensor.getDeviceAltitude]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ > 替代。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [sensor.getDeviceAltitude](arkts-sensorservice-sensor-getdevicealtitude-f.md#getdevicealtitude)(seaPressure:

<!--Device-sensor-function getAltitude(seaPressure: number, currentPressure: number, callback: AsyncCallback<number>): void--><!--Device-sensor-function getAltitude(seaPressure: number, currentPressure: number, callback: AsyncCallback<number>): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| seaPressure | number | 是 | 表示海平面气压值，单位为hPa。 |
| currentPressure | number | 是 | 表示设备所在高度的气压值，单位为hPa。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;number&gt; | 是 | 异步返回设备所在的海拔高度，单位为米。 |

**示例：**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

sensor.getAltitude(0, 200, (err: BusinessError, data: number) => {
  if (err) {
    console.error(`Failed to operate. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info("Succeeded in getting getAltitude interface get data: " + data);
});
```


## getAltitude

```TypeScript
function getAltitude(seaPressure: number, currentPressure: number): Promise<number>
```

根据气压值获取设备所在的海拔高度，使用Promise异步方式返回结果。 > **说明**： > > 从API version 8 开始支持，从API version 9 开始废弃，建议使用 > [sensor.getDeviceAltitude]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_替代。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [sensor.getDeviceAltitude](arkts-sensorservice-sensor-getdevicealtitude-f.md#getdevicealtitude)(seaPressure:

<!--Device-sensor-function getAltitude(seaPressure: number, currentPressure: number): Promise<number>--><!--Device-sensor-function getAltitude(seaPressure: number, currentPressure: number): Promise<number>-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| seaPressure | number | 是 | 表示海平面气压值，单位为hPa。 |
| currentPressure | number | 是 | 表示设备所在高度的气压值，单位为hPa。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | 使用异步方式返回设备所在的海拔高度（单位：米）。 |

**示例：**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

const promise = sensor.getAltitude(0, 200);
promise.then((data: number) => {
  console.info('Succeeded in getting sensor_getAltitude_Promise success', data);
}).catch((err: BusinessError) => {
  console.error(`Failed to operate.`);
})
```

