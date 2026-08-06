# offSensorStatusChange

## offSensorStatusChange

```TypeScript
function offSensorStatusChange(callback?: Callback<SensorStatusEvent>): void
```

Stop listening on device status changes.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-sensor-function offSensorStatusChange(callback?: Callback<SensorStatusEvent>): void--><!--Device-sensor-function offSensorStatusChange(callback?: Callback<SensorStatusEvent>): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;SensorStatusEvent&gt; | 否 | callback of sensor status. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_ 2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例：**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  const statusChangeCallback = (data: sensor.SensorStatusEvent) => {
    console.info('sensorStatusChange : ' + JSON.stringify(data));
  }
  const statusChangeCallback2 = (data: sensor.SensorStatusEvent) => {
    console.info('sensorStatusChange2 : ' + JSON.stringify(data));
  }
  // 注册两个设备上线消息监听回调
  sensor.onSensorStatusChange(statusChangeCallback);
  sensor.onSensorStatusChange(statusChangeCallback2);

  // 3秒后注销第一个监听
  setTimeout(() => {
    sensor.offSensorStatusChange(statusChangeCallback);
  }, 3000);
  // 5秒后注销所有监听
  setTimeout(() => {
    sensor.offSensorStatusChange();
  }, 5000);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke on. Code: ${e.code}, message: ${e.message}`);
}
```

