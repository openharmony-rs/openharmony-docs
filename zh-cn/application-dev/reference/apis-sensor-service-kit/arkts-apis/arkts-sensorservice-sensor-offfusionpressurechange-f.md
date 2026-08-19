# offFusionPressureChange

## 导入模块

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## offFusionPressureChange

```TypeScript
function offFusionPressureChange(sensorInfoParam?: SensorInfoParam, callback?: Callback<FusionPressureResponse>): void
```

Unsubscribe to fusion pressure sensor data, {@code SensorId.FUSION_PRESSURE}.

**起始版本：** 23

<!--Device-sensor-function offFusionPressureChange(sensorInfoParam?: SensorInfoParam, callback?: Callback<FusionPressureResponse>): void--><!--Device-sensor-function offFusionPressureChange(sensorInfoParam?: SensorInfoParam, callback?: Callback<FusionPressureResponse>): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| sensorInfoParam | [SensorInfoParam](arkts-sensorservice-sensor-sensorinfoparam-i.md) | 否 | Parameters of sensor on the device. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[FusionPressureResponse](arkts-sensorservice-sensor-fusionpressureresponse-i.md)&gt; | 否 | callback fusion pressure percent data. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception; <br> 2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.FusionPressureResponse) => {
  console.info(`callback response: ${JSON.stringify(response)}`);
}
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    // 订阅传感器事件
    sensor.onFusionPressureChange(sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.onFusionPressureChange. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}

function sensorUnsubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
  try {
    sensor.offFusionPressureChange(sensorInfoParam, sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.offFusionPressureChange. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}
```

