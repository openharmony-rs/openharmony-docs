# off_SensorId.SAR（系统接口）

## off_SensorId.SAR

```TypeScript
function off(type: SensorId.SAR, callback?: Callback<SarResponse>): void
```

取消订阅吸收比率传感器数据。调用后，SAR传感器的回调函数将不再触发。

**起始版本：** 10

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为10。

**废弃版本：** -1

<!--Device-sensor-function off(type: SensorId.SAR, callback?: Callback<SarResponse>): void--><!--Device-sensor-function off(type: SensorId.SAR, callback?: Callback<SarResponse>): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.SAR | 是 | 传感器类型，该值固定为SensorId.SAR。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[SarResponse](arkts-sensorservice-sensor-sarresponse-i-sys.md)&gt; | 否 | 需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission check failed. A non-system application uses the system API.<br>**适用版本：** 11+ |

## 示例

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

try {
  sensor.on(sensor.SensorId.SAR, callback1);
  sensor.on(sensor.SensorId.SAR, callback2);
  // 仅取消callback1的注册
  sensor.off(sensor.SensorId.SAR, callback1);
  // 取消注册SensorId.SAR的所有回调
  sensor.off(sensor.SensorId.SAR);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```


## off_SensorId.SAR

```TypeScript
function off(type: SensorId.SAR, sensorInfoParam?: SensorInfoParam, callback?: Callback<SarResponse>): void
```

取消订阅吸收比率传感器数据。与API version 10的off接口相比，新增sensorInfoParam参数，支持通过指定deviceId和sensorIndex来精确取消订阅某一设备上的特定传感器回调，适用于多设备场景。

**起始版本：** 19

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为19。

**废弃版本：** -1

<!--Device-sensor-function off(type: SensorId.SAR, sensorInfoParam?: SensorInfoParam, callback?: Callback<SarResponse>): void--><!--Device-sensor-function off(type: SensorId.SAR, sensorInfoParam?: SensorInfoParam, callback?: Callback<SarResponse>): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.SAR | 是 | 传感器类型，该值固定为SensorId.SAR。 |
| sensorInfoParam | [SensorInfoParam](arkts-sensorservice-sensor-sensorinfoparam-i.md) | 否 | 传感器传入设置参数，可指定deviceId和sensorIndex。默认值：deviceId为-1（本地设备），sensorIndex为0（默认传感器）。 不传入时默认取消本地设备上的回调。 |
| callback | [Callback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-callback-t.md)&lt;[SarResponse](arkts-sensorservice-sensor-sarresponse-i-sys.md)&gt; | 否 | 需要取消订阅的回调函数，若无此参数，则取消订阅指定设备上当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception; &lt;br&gt; 2. Sensor service ipc exception;3. Sensor data channel exception. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | Permission check failed. A non-system application uses the system API. |

## 示例

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.SarResponse) => {
  console.info(`callback response: ${JSON.stringify(response)}`);
}
// 传感器监听类型
const sensorType = sensor.SensorId.SAR;
const sensorInfoParam: sensor.SensorInfoParam = {};

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  try {
    // 查询所有的传感器
    const sensorList: sensor.Sensor[] = sensor.getSensorListSync();
    if (!sensorList.length) {
      return Ret.Failed;
    }
    // 根据实际业务逻辑获取目标传感器。
    const targetSensor = sensorList
      // 按需过滤deviceId为1、sensorId为2的所有传感器。此处示例仅做展示，开发者需要自行调整筛选逻辑。
      .filter((sensor: sensor.Sensor) => sensor.deviceId === 1 && sensor.sensorId === 2)
      // 可能存在的多个同类型传感器，选择sensorIndex为0的传感器。
      .find((sensor: sensor.Sensor) => sensor.sensorIndex === 0);
    if (!targetSensor) {
      return Ret.Failed;
    }
    sensorInfoParam.deviceId = targetSensor.deviceId;
    sensorInfoParam.sensorIndex = targetSensor.sensorIndex;
    // 订阅传感器事件
    sensor.on(sensorType, sensorCallback, { sensorInfoParam });
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.on. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}

function sensorUnsubscribe(): Ret {
  let ret: Ret = Ret.OK;
  try {
    sensor.off(sensorType, sensorInfoParam, sensorCallback);
  } catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke sensor.off. Code: ${e.code}, message: ${e.message}`);
    ret = Ret.Failed;
  }
  return ret;
}
```

