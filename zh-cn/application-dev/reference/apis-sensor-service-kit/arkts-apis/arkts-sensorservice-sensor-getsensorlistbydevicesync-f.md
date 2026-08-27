# getSensorListByDeviceSync

## 导入模块

```TypeScript
```

## getSensorListByDeviceSync

```TypeScript
function getSensorListByDeviceSync(deviceId?: number): Array<Sensor>
```

同步获取设备的所有传感器信息。getSensorListByDeviceSync返回设备上所有传感器信息，getSingleSensorByDeviceSync返回指定单个传感器信息。

**起始版本：** 19

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | number | 否 | 设备ID，默认为查询本地设备，默认值为-1，表示本地设备，设备ID需通过 [getSensorList](arkts-sensorservice-sensor-getsensorlist-f.md)查询或者监听设备上下线接口 [sensorStatusChange](arkts-sensorservice-sensor-on-f.md#onsensorstatuschange)获取。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array & lt;Sensor & gt; | 传感器属性列表。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  const deviceId = 1;
  // 第一个参数deviceId 非必填
  const sensorList: sensor.Sensor[] = sensor.getSensorListByDeviceSync(deviceId);
  console.info(`sensorList length: ${sensorList.length}`);
  console.info(`sensorList: ${JSON.stringify(sensorList)}`);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get sensorList. Code: ${e.code}, message: ${e.message}`);
}
```
