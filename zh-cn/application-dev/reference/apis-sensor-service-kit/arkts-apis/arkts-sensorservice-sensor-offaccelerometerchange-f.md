# offAccelerometerChange

## offAccelerometerChange

```TypeScript
function offAccelerometerChange(sensorInfoParam?: SensorInfoParam, callback?: Callback<AccelerometerResponse>): void
```

Unsubscribe to accelerometer sensor data, {@code SensorId.ACCELEROMETER}.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**需要权限：** ohos.permission.ACCELEROMETER

<!--Device-sensor-function offAccelerometerChange(sensorInfoParam?: SensorInfoParam, callback?: Callback<AccelerometerResponse>): void--><!--Device-sensor-function offAccelerometerChange(sensorInfoParam?: SensorInfoParam, callback?: Callback<AccelerometerResponse>): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sensorInfoParam | [SensorInfoParam](arkts-sensorservice-sensor-sensorinfoparam-i.md) | 否 | Parameters of sensor on the device. |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;AccelerometerResponse&gt; | 否 | callback accelerometer data. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception; &lt;br&gt; 2. Sensor service ipc exception;3. Sensor data channel exception. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

## 示例

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.AccelerometerResponse) => {
  console.info(`callback response: ${JSON.stringify(response)}`);
}
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    // 订阅传感器事件
    sensor.onAccelerometerChange(sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.onAccelerometerChange. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}

function sensorUnsubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    sensor.offAccelerometerChange(sensorInfoParam, sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.offAccelerometerChange. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}
```

