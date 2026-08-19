# getSingleSensorByDeviceSync

## 导入模块

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## getSingleSensorByDeviceSync

```TypeScript
function getSingleSensorByDeviceSync(type: SensorId, deviceId?: int): Array<Sensor>
```

同步获取指定设备和类型的传感器信息。如果存在外设且未指定设备ID，获取到的传感器将是所有符合指定传感器类型的本地和外设传感器。如果不存在外设，则仅获取本地的传感器。

**起始版本：** 23

<!--Device-sensor-function getSingleSensorByDeviceSync(type: SensorId, deviceId?: int): Array<Sensor>--><!--Device-sensor-function getSingleSensorByDeviceSync(type: SensorId, deviceId?: int): Array<Sensor>-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | [SensorId](arkts-sensorservice-sensor-sensorid-e.md) | 是 | 指定传感器类型。 |
| deviceId | int | 否 | 设备ID，默认为查询本地设备，默认值为-1，表示本地设备，设备ID需通过 [getSensorList](arkts-sensorservice-sensor-getsensorlist-f.md)查询或者监听设备上下线接口 [sensorStatusChange](arkts-sensorservice-sensor-onsensorstatuschange-f.md)获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;Sensor&gt; | 传感器属性列表。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  const deviceId = 1;
  // 第二个参数deviceId 非必填
  const sensorList: sensor.Sensor[] = sensor.getSingleSensorByDeviceSync(sensor.SensorId.ACCELEROMETER, deviceId);
  console.info(`sensorList length: ${sensorList.length}`);
  console.info(`sensorList Json: ${JSON.stringify(sensorList)}`);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get sensorList. Code: ${e.code}, message: ${e.message}`);
}
```

