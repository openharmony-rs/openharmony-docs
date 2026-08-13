# getSensorListSync

## getSensorListSync

```TypeScript
function getSensorListSync(): Array<Sensor>
```

获取设备上的所有传感器信息，使用同步方式返回结果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-sensor-function getSensorListSync(): Array<Sensor>--><!--Device-sensor-function getSensorListSync(): Array<Sensor>-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;Sensor&gt; | 使用同步方式返回传感器属性列表。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception; &lt;br&gt; 2. Sensor service ipc exception;3. Sensor data channel exception. |

## 示例

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  let ret = sensor.getSensorListSync()
  for (let i = 0; i < ret.length; i++) {
    console.info('Succeeded in getting sensor: ' + JSON.stringify(ret[i]));
  }
} catch(error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to get singleSensor . Code: ${e.code}, message: ${e.message}`);
}
```

