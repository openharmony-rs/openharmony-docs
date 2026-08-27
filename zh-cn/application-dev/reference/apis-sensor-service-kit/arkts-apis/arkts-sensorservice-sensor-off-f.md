# off

## 导入模块

```TypeScript
```

## off

```TypeScript
function off(type: SensorId.ACCELEROMETER, callback?: Callback<AccelerometerResponse>): void
```

取消订阅加速度传感器数据。当不再需要接收加速度传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。

**起始版本：** 9

**需要权限：** ohos.permission.ACCELEROMETER

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.ACCELEROMETER | 是 | 传感器类型，该值固定为SensorId.ACCELEROMETER。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;AccelerometerResponse&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;   2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.ACCELEROMETER, callback1);
  sensor.on(sensor.SensorId.ACCELEROMETER, callback2);
  // 仅取消callback1的注册
  sensor.off(sensor.SensorId.ACCELEROMETER, callback1);
  // 取消SensorId.ACCELEROMETER类型的所有回调
  sensor.off(sensor.SensorId.ACCELEROMETER);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```


## off

```TypeScript
function off(type: SensorId.ACCELEROMETER, sensorInfoParam?: SensorInfoParam, callback?: Callback<AccelerometerResponse>): void
```

取消订阅加速度传感器数据。当不再需要接收加速度传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。

**起始版本：** 19

**需要权限：** ohos.permission.ACCELEROMETER

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.ACCELEROMETER | 是 | 传感器类型，该值固定为SensorId.ACCELEROMETER。 |
| sensorInfoParam | [SensorInfoParam](arkts-sensorservice-sensor-sensorinfoparam-i.md) | 否 | 传感器传入设置参数，可指定deviceId和sensorIndex，用于取消指定设备上指定传感器的订阅。不传入时默认取消本地设备该类型所有传感器的订阅。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;AccelerometerResponse&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception;   2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.AccelerometerResponse) => {
  console.info(`callback response: ${JSON.stringify(response)}`);
}
// 传感器监听类别
const sensorType = sensor.SensorId.ACCELEROMETER;
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
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
  // 使用try catch对可能出现的异常进行捕获
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


## off

```TypeScript
function off(type: SensorId.ACCELEROMETER_UNCALIBRATED, callback?: Callback<AccelerometerUncalibratedResponse>): void
```

取消订阅未校准加速度传感器数据。当不再需要接收未校准加速度传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。

**起始版本：** 9

**需要权限：** ohos.permission.ACCELEROMETER

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.ACCELEROMETER_UNCALIBRATED | 是 | 传感器类型，该值固定为SensorId.ACCELEROMETER_UNCALIBRATED。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AccelerometerUncalibratedResponse](arkts-sensorservice-sensor-accelerometeruncalibratedresponse-i.md)&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;   2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.ACCELEROMETER_UNCALIBRATED, callback1);
  sensor.on(sensor.SensorId.ACCELEROMETER_UNCALIBRATED, callback2);
  // 仅取消callback1的注册
  sensor.off(sensor.SensorId.ACCELEROMETER_UNCALIBRATED, callback1);
  // 取消注册SensorId.ACCELEROMETER_UNCALIBRATED类型的所有回调
  sensor.off(sensor.SensorId.ACCELEROMETER_UNCALIBRATED);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```


## off

```TypeScript
function off(type: SensorId.ACCELEROMETER_UNCALIBRATED, sensorInfoParam?: SensorInfoParam, callback?: Callback<AccelerometerUncalibratedResponse>): void
```

取消订阅未校准加速度传感器数据。当不再需要接收未校准加速度传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。

**起始版本：** 19

**需要权限：** ohos.permission.ACCELEROMETER

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.ACCELEROMETER_UNCALIBRATED | 是 | 传感器类型，该值固定为SensorId.ACCELEROMETER_UNCALIBRATED。 |
| sensorInfoParam | [SensorInfoParam](arkts-sensorservice-sensor-sensorinfoparam-i.md) | 否 | 传感器传入设置参数，可指定deviceId和sensorIndex，用于取消指定设备上指定传感器的订阅。不传入时默认取消本地设备该类型所有传感器的订阅。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AccelerometerUncalibratedResponse](arkts-sensorservice-sensor-accelerometeruncalibratedresponse-i.md)&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception;   2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.AccelerometerUncalibratedResponse) => {
  console.info(`callback response: ${JSON.stringify(response)}`);
}
// 传感器监听类型
const sensorType = sensor.SensorId.ACCELEROMETER_UNCALIBRATED;
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
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
  // 使用try catch对可能出现的异常进行捕获
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


## off

```TypeScript
function off(type: SensorId.AMBIENT_LIGHT, callback?: Callback<LightResponse>): void
```

取消订阅环境光传感器数据。当不再需要接收环境光传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.AMBIENT_LIGHT | 是 | 传感器类型，该值固定为SensorId.AMBIENT_LIGHT。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;LightResponse&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;   2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.AMBIENT_LIGHT, callback1);
  sensor.on(sensor.SensorId.AMBIENT_LIGHT, callback2);
  // 仅取消callback1的注册
  sensor.off(sensor.SensorId.AMBIENT_LIGHT, callback1);
  // 取消注册SensorId.AMBIENT_LIGHT
  sensor.off(sensor.SensorId.AMBIENT_LIGHT);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```


## off

```TypeScript
function off(type: SensorId.AMBIENT_LIGHT, sensorInfoParam?: SensorInfoParam, callback?: Callback<LightResponse>): void
```

取消订阅环境光传感器数据。当不再需要接收环境光传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。

**起始版本：** 19

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.AMBIENT_LIGHT | 是 | 传感器类型，该值固定为SensorId.AMBIENT_LIGHT。 |
| sensorInfoParam | [SensorInfoParam](arkts-sensorservice-sensor-sensorinfoparam-i.md) | 否 | 传感器传入设置参数，可指定deviceId和sensorIndex，用于取消指定设备上指定传感器的订阅。不传入时默认取消本地设备该类型所有传感器的订阅。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;LightResponse&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception;   2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.LightResponse) => {
  console.info(`callback response: ${JSON.stringify(response)}`);
}
// 传感器监听类型
const sensorType = sensor.SensorId.AMBIENT_LIGHT;
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
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
  // 使用try catch对可能出现的异常进行捕获
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


## off

```TypeScript
function off(type: SensorId.AMBIENT_TEMPERATURE, callback?: Callback<AmbientTemperatureResponse>): void
```

取消订阅温度传感器数据。当不再需要接收温度传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.AMBIENT_TEMPERATURE | 是 | 传感器类型，该值固定为SensorId.AMBIENT_TEMPERATURE。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AmbientTemperatureResponse](arkts-sensorservice-sensor-ambienttemperatureresponse-i.md)&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;   2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.AMBIENT_TEMPERATURE, callback1);
  sensor.on(sensor.SensorId.AMBIENT_TEMPERATURE, callback2);
  // 仅取消callback1的注册
  sensor.off(sensor.SensorId.AMBIENT_TEMPERATURE, callback1);
  // 取消注册SensorId.AMBIENT_TEMPERATURE的所有回调
  sensor.off(sensor.SensorId.AMBIENT_TEMPERATURE);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```


## off

```TypeScript
function off(type: SensorId.AMBIENT_TEMPERATURE, sensorInfoParam?: SensorInfoParam, callback?: Callback<AmbientTemperatureResponse>): void
```

取消订阅温度传感器数据。当不再需要接收温度传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。

**起始版本：** 19

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.AMBIENT_TEMPERATURE | 是 | 传感器类型，该值固定为SensorId.AMBIENT_TEMPERATURE。 |
| sensorInfoParam | [SensorInfoParam](arkts-sensorservice-sensor-sensorinfoparam-i.md) | 否 | 传感器传入设置参数，可指定deviceId和sensorIndex，用于取消指定设备上指定传感器的订阅。不传入时默认取消本地设备该类型所有传感器的订阅。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AmbientTemperatureResponse](arkts-sensorservice-sensor-ambienttemperatureresponse-i.md)&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception;   2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.AmbientTemperatureResponse) => {
  console.info(`callback response: ${JSON.stringify(response)}`);
}
// 传感器监听类型
const sensorType = sensor.SensorId.AMBIENT_TEMPERATURE;
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
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
  // 使用try catch对可能出现的异常进行捕获
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


## off

```TypeScript
function off(type: SensorId.BAROMETER, callback?: Callback<BarometerResponse>): void
```

取消订阅气压计传感器数据。当不再需要接收气压计传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.BAROMETER | 是 | 传感器类型，该值固定为SensorId.BAROMETER。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;BarometerResponse&gt; | 否 |  |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;   2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
    console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
    console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// 使用try catch对可能出现的异常进行捕获
try {
    sensor.on(sensor.SensorId.BAROMETER, callback1);
    sensor.on(sensor.SensorId.BAROMETER, callback2);
    // 仅取消callback1的注册
    sensor.off(sensor.SensorId.BAROMETER, callback1);
    // 取消注册SensorId.BAROMETER的所有回调
    sensor.off(sensor.SensorId.BAROMETER);
} catch (error) {
    let e: BusinessError = error as BusinessError;
    console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```


## off

```TypeScript
function off(type: SensorId.BAROMETER, sensorInfoParam?: SensorInfoParam, callback?: Callback<BarometerResponse>): void
```

取消订阅气压计传感器数据。当不再需要接收气压计传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。

**起始版本：** 19

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.BAROMETER | 是 | 传感器类型，该值固定为SensorId.BAROMETER。 |
| sensorInfoParam | [SensorInfoParam](arkts-sensorservice-sensor-sensorinfoparam-i.md) | 否 | 传感器传入设置参数，可指定deviceId和sensorIndex，用于取消指定设备上指定传感器的订阅。不传入时默认取消本地设备该类型所有传感器的订阅。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;BarometerResponse&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception;   2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.BarometerResponse) => {
  console.info(`callback response: ${JSON.stringify(response)}`);
}
// 传感器监听类型
const sensorType = sensor.SensorId.BAROMETER;
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
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
  // 使用try catch对可能出现的异常进行捕获
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


## off

```TypeScript
function off(type: SensorId.GRAVITY, callback?: Callback<GravityResponse>): void
```

取消订阅重力传感器数据。当不再需要接收重力传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.GRAVITY | 是 | 传感器类型，该值固定为SensorId.GRAVITY。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[GravityResponse](arkts-sensorservice-sensor-gravityresponse-i.md)&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;   2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.GRAVITY, callback1);
  sensor.on(sensor.SensorId.GRAVITY, callback2);
  // 仅取消callback1的注册
  sensor.off(sensor.SensorId.GRAVITY, callback1);
  // 取消注册SensorId.GRAVITY的所有回调
  sensor.off(sensor.SensorId.GRAVITY);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```


## off

```TypeScript
function off(type: SensorId.GRAVITY, sensorInfoParam?: SensorInfoParam, callback?: Callback<GravityResponse>): void
```

取消订阅重力传感器数据。当不再需要接收重力传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。

**起始版本：** 19

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.GRAVITY | 是 | 传感器类型，该值固定为SensorId.GRAVITY。 |
| sensorInfoParam | [SensorInfoParam](arkts-sensorservice-sensor-sensorinfoparam-i.md) | 否 | 传感器传入设置参数，可指定deviceId和sensorIndex，用于取消指定设备上指定传感器的订阅。不传入时默认取消本地设备该类型所有传感器的订阅。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[GravityResponse](arkts-sensorservice-sensor-gravityresponse-i.md)&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception;   2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.GravityResponse) => {
  console.info(`callback response: ${JSON.stringify(response)}`);
}
// 传感器监听类型
const sensorType = sensor.SensorId.GRAVITY;
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
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
  // 使用try catch对可能出现的异常进行捕获
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


## off

```TypeScript
function off(type: SensorId.GYROSCOPE, callback?: Callback<GyroscopeResponse>): void
```

取消订阅陀螺仪传感器数据。当不再需要接收陀螺仪传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。

**起始版本：** 9

**需要权限：** ohos.permission.GYROSCOPE

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.GYROSCOPE | 是 | 传感器类型，该值固定为SensorId.GYROSCOPE。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;GyroscopeResponse&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;   2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.GYROSCOPE, callback1);
  sensor.on(sensor.SensorId.GYROSCOPE, callback2);
  // 仅取消callback1的注册
  sensor.off(sensor.SensorId.GYROSCOPE, callback1);
  // 取消注册SensorId.GYROSCOPE的所有回调
  sensor.off(sensor.SensorId.GYROSCOPE);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```


## off

```TypeScript
function off(type: SensorId.GYROSCOPE, sensorInfoParam?: SensorInfoParam, callback?: Callback<GyroscopeResponse>): void
```

取消订阅陀螺仪传感器数据。当不再需要接收陀螺仪传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。

**起始版本：** 19

**需要权限：** ohos.permission.GYROSCOPE

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.GYROSCOPE | 是 | 传感器类型，该值固定为SensorId.GYROSCOPE。 |
| sensorInfoParam | [SensorInfoParam](arkts-sensorservice-sensor-sensorinfoparam-i.md) | 否 | 传感器传入设置参数，可指定deviceId和sensorIndex，用于取消指定设备上指定传感器的订阅。不传入时默认取消本地设备该类型所有传感器的订阅。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;GyroscopeResponse&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception;   2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.GyroscopeResponse) => {
  console.info(`callback response: ${JSON.stringify(response)}`);
}
// 传感器监听类型
const sensorType = sensor.SensorId.GYROSCOPE;
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
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
  // 使用try catch对可能出现的异常进行捕获
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


## off

```TypeScript
function off(type: SensorId.GYROSCOPE_UNCALIBRATED, callback?: Callback<GyroscopeUncalibratedResponse>): void
```

取消订阅未校准陀螺仪传感器数据。当不再需要接收未校准陀螺仪传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。

**起始版本：** 9

**需要权限：** ohos.permission.GYROSCOPE

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.GYROSCOPE_UNCALIBRATED | 是 | 传感器类型，该值固定为SensorId.GYROSCOPE_UNCALIBRATED。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[GyroscopeUncalibratedResponse](arkts-sensorservice-sensor-gyroscopeuncalibratedresponse-i.md)&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;   2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.GYROSCOPE_UNCALIBRATED, callback1);
  sensor.on(sensor.SensorId.GYROSCOPE_UNCALIBRATED, callback2);
  // 仅取消callback1的注册
  sensor.off(sensor.SensorId.GYROSCOPE_UNCALIBRATED, callback1);
  // 取消注册SensorId.GYROSCOPE_UNCALIBRATED的所有回调
  sensor.off(sensor.SensorId.GYROSCOPE_UNCALIBRATED);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```


## off

```TypeScript
function off(type: SensorId.GYROSCOPE_UNCALIBRATED, sensorInfoParam?: SensorInfoParam, callback?: Callback<GyroscopeUncalibratedResponse>): void
```

取消订阅未校准陀螺仪传感器数据。

**起始版本：** 19

**需要权限：** ohos.permission.GYROSCOPE

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.GYROSCOPE_UNCALIBRATED | 是 | 传感器类型，该值固定为SensorId.GYROSCOPE_UNCALIBRATED。 |
| sensorInfoParam | [SensorInfoParam](arkts-sensorservice-sensor-sensorinfoparam-i.md) | 否 | 传感器传入设置参数，可指定deviceId和sensorIndex，用于取消指定设备上指定传感器的订阅。不传入时默认取消本地设备该类型所有传感器的订阅。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[GyroscopeUncalibratedResponse](arkts-sensorservice-sensor-gyroscopeuncalibratedresponse-i.md)&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception;   2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.GyroscopeUncalibratedResponse) => {
  console.info(`callback response: ${JSON.stringify(response)}`);
}
// 传感器监听类型
const sensorType = sensor.SensorId.GYROSCOPE_UNCALIBRATED;
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
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
  // 使用try catch对可能出现的异常进行捕获
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


## off

```TypeScript
function off(type: SensorId.HALL, callback?: Callback<HallResponse>): void
```

取消订阅霍尔传感器数据。当不再需要接收霍尔传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.HALL | 是 | 传感器类型，该值固定为SensorId.HALL。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[HallResponse](arkts-sensorservice-sensor-hallresponse-i.md)&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;   2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.HALL, callback1);
  sensor.on(sensor.SensorId.HALL, callback2);
  // 仅取消callback1的注册
  sensor.off(sensor.SensorId.HALL, callback1);
  // 取消注册SensorId.HALL的所有回调
  sensor.off(sensor.SensorId.HALL);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```


## off

```TypeScript
function off(type: SensorId.HALL, sensorInfoParam?: SensorInfoParam, callback?: Callback<HallResponse>): void
```

取消订阅霍尔传感器数据。当不再需要接收霍尔传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。

**起始版本：** 19

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.HALL | 是 | 传感器类型，该值固定为SensorId.HALL。 |
| sensorInfoParam | [SensorInfoParam](arkts-sensorservice-sensor-sensorinfoparam-i.md) | 否 | 传感器传入设置参数，可指定deviceId和sensorIndex，用于取消指定设备上指定传感器的订阅。不传入时默认取消本地设备该类型所有传感器的订阅。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[HallResponse](arkts-sensorservice-sensor-hallresponse-i.md)&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception;   2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.HallResponse) => {
  console.info(`callback response: ${JSON.stringify(response)}`);
}
// 传感器监听类型
const sensorType = sensor.SensorId.HALL;
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
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
  // 使用try catch对可能出现的异常进行捕获
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


## off

```TypeScript
function off(type: SensorId.HEART_RATE, callback?: Callback<HeartRateResponse>): void
```

取消订阅心率传感器数据。当不再需要接收心率传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。

**起始版本：** 9

**需要权限：** ohos.permission.READ_HEALTH_DATA

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.HEART_RATE | 是 | 传感器类型，该值固定为SensorId.HEART_RATE。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;HeartRateResponse&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;   2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.HEART_RATE, callback1);
  sensor.on(sensor.SensorId.HEART_RATE, callback2);
  // 仅取消callback1的注册
  sensor.off(sensor.SensorId.HEART_RATE, callback1);
  // 取消注册SensorId.HEART_RATE的所有回调
  sensor.off(sensor.SensorId.HEART_RATE);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```


## off

```TypeScript
function off(type: SensorId.HEART_RATE, sensorInfoParam?: SensorInfoParam, callback?: Callback<HeartRateResponse>): void
```

取消订阅心率传感器数据。当不再需要接收心率传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。

**起始版本：** 19

**需要权限：** ohos.permission.READ_HEALTH_DATA

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.HEART_RATE | 是 | 传感器类型，该值固定为SensorId.HEART_RATE。 |
| sensorInfoParam | [SensorInfoParam](arkts-sensorservice-sensor-sensorinfoparam-i.md) | 否 | 传感器传入设置参数，可指定deviceId和sensorIndex，用于取消指定设备上指定传感器的订阅。不传入时默认取消本地设备该类型所有传感器的订阅。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;HeartRateResponse&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception;   2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.HeartRateResponse) => {
  console.info(`callback response: ${JSON.stringify(response)}`);
}
// 传感器监听类型
const sensorType = sensor.SensorId.HEART_RATE;
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
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
  // 使用try catch对可能出现的异常进行捕获
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


## off

```TypeScript
function off(type: SensorId.HUMIDITY, callback?: Callback<HumidityResponse>): void
```

取消订阅湿度传感器数据。当不再需要接收湿度传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.HUMIDITY | 是 | 传感器类型，该值固定为SensorId.HUMIDITY。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[HumidityResponse](arkts-sensorservice-sensor-humidityresponse-i.md)&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;   2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.HUMIDITY, callback1);
  sensor.on(sensor.SensorId.HUMIDITY, callback2);
  // 仅取消callback1的注册
  sensor.off(sensor.SensorId.HUMIDITY, callback1);
  // 取消注册SensorId.HUMIDITY的所有回调
  sensor.off(sensor.SensorId.HUMIDITY);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```


## off

```TypeScript
function off(type: SensorId.HUMIDITY, sensorInfoParam?: SensorInfoParam, callback?: Callback<HumidityResponse>): void
```

取消订阅湿度传感器数据。当不再需要接收湿度传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。

**起始版本：** 19

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.HUMIDITY | 是 | 传感器类型，该值固定为SensorId.HUMIDITY。 |
| sensorInfoParam | [SensorInfoParam](arkts-sensorservice-sensor-sensorinfoparam-i.md) | 否 | 传感器传入设置参数，可指定deviceId和sensorIndex，用于取消指定设备上指定传感器的订阅。不传入时默认取消本地设备该类型所有传感器的订阅。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[HumidityResponse](arkts-sensorservice-sensor-humidityresponse-i.md)&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception;   2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.HumidityResponse) => {
  console.info(`callback response: ${JSON.stringify(response)}`);
}
// 传感器监听类型
const sensorType = sensor.SensorId.HUMIDITY;
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
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
  // 使用try catch对可能出现的异常进行捕获
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


## off

```TypeScript
function off(type: SensorId.LINEAR_ACCELEROMETER, callback?: Callback<LinearAccelerometerResponse>): void
```

取消订阅线性加速度传感器数据。当不再需要接收线性加速度传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。

**起始版本：** 9

**需要权限：** ohos.permission.ACCELEROMETER

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.LINEAR_ACCELEROMETER | 是 | 传感器类型，该值固定为SensorId.LINEAR_ACCELEROMETER。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[LinearAccelerometerResponse](arkts-sensorservice-sensor-linearaccelerometerresponse-i.md)&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;   2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.LINEAR_ACCELEROMETER, callback1);
  sensor.on(sensor.SensorId.LINEAR_ACCELEROMETER, callback2);
  // 仅取消callback1的注册
  sensor.off(sensor.SensorId.LINEAR_ACCELEROMETER, callback1);
  // 取消注册SensorId.LINEAR_ACCELEROMETER的所有回调
  sensor.off(sensor.SensorId.LINEAR_ACCELEROMETER);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```


## off

```TypeScript
function off(type: SensorId.LINEAR_ACCELEROMETER, sensorInfoParam?: SensorInfoParam, callback?: Callback<LinearAccelerometerResponse>): void
```

取消订阅线性加速度传感器数据。当不再需要接收线性加速度传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。

**起始版本：** 19

**需要权限：** ohos.permission.ACCELEROMETER

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.LINEAR_ACCELEROMETER | 是 | 传感器类型，该值固定为SensorId.LINEAR_ACCELEROMETER。 |
| sensorInfoParam | [SensorInfoParam](arkts-sensorservice-sensor-sensorinfoparam-i.md) | 否 | 传感器传入设置参数，可指定deviceId和sensorIndex，用于取消指定设备上指定传感器的订阅。不传入时默认取消本地设备该类型所有传感器的订阅。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[LinearAccelerometerResponse](arkts-sensorservice-sensor-linearaccelerometerresponse-i.md)&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception;   2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.LinearAccelerometerResponse) => {
  console.info(`callback response: ${JSON.stringify(response)}`);
}
// 传感器监听类型
const sensorType = sensor.SensorId.LINEAR_ACCELEROMETER;
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
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
  // 使用try catch对可能出现的异常进行捕获
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


## off

```TypeScript
function off(type: SensorId.MAGNETIC_FIELD, callback?: Callback<MagneticFieldResponse>): void
```

取消订阅磁场传感器数据。当不再需要接收磁场传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.MAGNETIC_FIELD | 是 | 传感器类型，该值固定为SensorId.MAGNETIC_FIELD。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[MagneticFieldResponse](arkts-sensorservice-sensor-magneticfieldresponse-i.md)&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;   2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.MAGNETIC_FIELD, callback1);
  sensor.on(sensor.SensorId.MAGNETIC_FIELD, callback2);
  // 仅取消callback1的注册
  sensor.off(sensor.SensorId.MAGNETIC_FIELD, callback1);
  // 取消注册SensorId.MAGNETIC_FIELD的所有回调
  sensor.off(sensor.SensorId.MAGNETIC_FIELD);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```


## off

```TypeScript
function off(type: SensorId.MAGNETIC_FIELD, sensorInfoParam?: SensorInfoParam, callback?: Callback<MagneticFieldResponse>): void
```

取消订阅磁场传感器数据。当不再需要接收磁场传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。

**起始版本：** 19

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.MAGNETIC_FIELD | 是 | 传感器类型，该值固定为SensorId.MAGNETIC_FIELD。 |
| sensorInfoParam | [SensorInfoParam](arkts-sensorservice-sensor-sensorinfoparam-i.md) | 否 | 传感器传入设置参数，可指定deviceId和sensorIndex，用于取消指定设备上指定传感器的订阅。不传入时默认取消本地设备该类型所有传感器的订阅。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[MagneticFieldResponse](arkts-sensorservice-sensor-magneticfieldresponse-i.md)&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception;   2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.MagneticFieldResponse) => {
  console.info(`callback response: ${JSON.stringify(response)}`);
}
// 传感器监听类型
const sensorType = sensor.SensorId.MAGNETIC_FIELD;
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
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
  // 使用try catch对可能出现的异常进行捕获
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


## off

```TypeScript
function off(type: SensorId.MAGNETIC_FIELD_UNCALIBRATED, callback?: Callback<MagneticFieldUncalibratedResponse>): void
```

取消订阅未校准的磁场传感器数据。当不再需要接收未校准磁场传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.MAGNETIC_FIELD_UNCALIBRATED | 是 | 传感器类型，该值固定为SensorId.MAGNETIC_FIELD_UNCALIBRATED。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[MagneticFieldUncalibratedResponse](arkts-sensorservice-sensor-magneticfielduncalibratedresponse-i.md)&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;   2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.MAGNETIC_FIELD_UNCALIBRATED, callback1);
  sensor.on(sensor.SensorId.MAGNETIC_FIELD_UNCALIBRATED, callback2);
  // 仅取消callback1的注册
  sensor.off(sensor.SensorId.MAGNETIC_FIELD_UNCALIBRATED, callback1);
  // 取消注册SensorId.MAGNETIC_FIELD_UNCALIBRATED的所有回调
  sensor.off(sensor.SensorId.MAGNETIC_FIELD_UNCALIBRATED);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```


## off

```TypeScript
function off(type: SensorId.MAGNETIC_FIELD_UNCALIBRATED, sensorInfoParam?: SensorInfoParam, callback?: Callback<MagneticFieldUncalibratedResponse>): void
```

取消订阅未校准的磁场传感器数据。当不再需要接收未校准磁场传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。

**起始版本：** 19

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.MAGNETIC_FIELD_UNCALIBRATED | 是 | 传感器类型，该值固定为SensorId.MAGNETIC_FIELD_UNCALIBRATED。 |
| sensorInfoParam | [SensorInfoParam](arkts-sensorservice-sensor-sensorinfoparam-i.md) | 否 | 传感器传入设置参数，可指定deviceId和sensorIndex，用于取消指定设备上指定传感器的订阅。不传入时默认取消本地设备该类型所有传感器的订阅。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[MagneticFieldUncalibratedResponse](arkts-sensorservice-sensor-magneticfielduncalibratedresponse-i.md)&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception;   2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.MagneticFieldUncalibratedResponse) => {
  console.info(`callback response: ${JSON.stringify(response)}`);
}
// 传感器监听类型
const sensorType = sensor.SensorId.MAGNETIC_FIELD_UNCALIBRATED;
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
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
  // 使用try catch对可能出现的异常进行捕获
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


## off

```TypeScript
function off(type: SensorId.ORIENTATION, callback?: Callback<OrientationResponse>): void
```

取消订阅方向传感器数据。当不再需要接收方向传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.ORIENTATION | 是 | 传感器类型，该值固定为SensorId.ORIENTATION。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[OrientationResponse](arkts-sensorservice-sensor-orientationresponse-i.md)&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;   2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.ORIENTATION, callback1);
  sensor.on(sensor.SensorId.ORIENTATION, callback2);
  // 仅取消callback1的注册
  sensor.off(sensor.SensorId.ORIENTATION, callback1);
  // 取消注册SensorId.ORIENTATION的所有回调
  sensor.off(sensor.SensorId.ORIENTATION);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```


## off

```TypeScript
function off(type: SensorId.ORIENTATION, sensorInfoParam?: SensorInfoParam, callback?: Callback<OrientationResponse>): void
```

取消订阅方向传感器数据。当不再需要接收方向传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。

**起始版本：** 19

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.ORIENTATION | 是 | 传感器类型，该值固定为SensorId.ORIENTATION。 |
| sensorInfoParam | [SensorInfoParam](arkts-sensorservice-sensor-sensorinfoparam-i.md) | 否 | 传感器传入设置参数，可指定deviceId和sensorIndex，用于取消指定设备上指定传感器的订阅。不传入时默认取消本地设备该类型所有传感器的订阅。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[OrientationResponse](arkts-sensorservice-sensor-orientationresponse-i.md)&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception;   2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.OrientationResponse) => {
  console.info(`callback response: ${JSON.stringify(response)}`);
}
// 传感器监听类型
const sensorType = sensor.SensorId.ORIENTATION;
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
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
  // 使用try catch对可能出现的异常进行捕获
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


## off

```TypeScript
function off(type: SensorId.PEDOMETER, callback?: Callback<PedometerResponse>): void
```

取消订阅计步器传感器数据。当不再需要接收计步器传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。

**起始版本：** 9

**需要权限：** ohos.permission.ACTIVITY_MOTION

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.PEDOMETER | 是 | 传感器类型，该值固定为SensorId.PEDOMETER。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PedometerResponse](arkts-sensorservice-sensor-pedometerresponse-i.md)&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;   2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.PEDOMETER, callback1);
  sensor.on(sensor.SensorId.PEDOMETER, callback2);
  // 仅取消callback1的注册
  sensor.off(sensor.SensorId.PEDOMETER, callback1);
  // 取消注册SensorId.PEDOMETER的所有回调
  sensor.off(sensor.SensorId.PEDOMETER);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```


## off

```TypeScript
function off(type: SensorId.PEDOMETER, sensorInfoParam?: SensorInfoParam, callback?: Callback<PedometerResponse>): void
```

取消订阅计步器传感器数据。当不再需要接收计步器传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。

**起始版本：** 19

**需要权限：** ohos.permission.ACTIVITY_MOTION

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.PEDOMETER | 是 | 传感器类型，该值固定为SensorId.PEDOMETER。 |
| sensorInfoParam | [SensorInfoParam](arkts-sensorservice-sensor-sensorinfoparam-i.md) | 否 | 传感器传入设置参数，可指定deviceId和sensorIndex，用于取消指定设备上指定传感器的订阅。不传入时默认取消本地设备该类型所有传感器的订阅。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PedometerResponse](arkts-sensorservice-sensor-pedometerresponse-i.md)&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception;   2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.PedometerResponse) => {
  console.info(`callback response: ${JSON.stringify(response)}`);
}
// 传感器监听类型
const sensorType = sensor.SensorId.PEDOMETER;
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
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
  // 使用try catch对可能出现的异常进行捕获
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


## off

```TypeScript
function off(type: SensorId.PEDOMETER_DETECTION, callback?: Callback<PedometerDetectionResponse>): void
```

取消订阅计步检测器传感器数据。当不再需要接收计步检测器传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。

**起始版本：** 9

**需要权限：** ohos.permission.ACTIVITY_MOTION

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.PEDOMETER_DETECTION | 是 | 传感器类型，该值固定为SensorId.PEDOMETER_DETECTION。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PedometerDetectionResponse](arkts-sensorservice-sensor-pedometerdetectionresponse-i.md)&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;   2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.PEDOMETER_DETECTION, callback1);
  sensor.on(sensor.SensorId.PEDOMETER_DETECTION, callback2);
  // 仅取消callback1的注册
  sensor.off(sensor.SensorId.PEDOMETER_DETECTION, callback1);
  // 取消注册SensorId.PEDOMETER_DETECTION的所有回调
  sensor.off(sensor.SensorId.PEDOMETER_DETECTION);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```


## off

```TypeScript
function off(type: SensorId.PEDOMETER_DETECTION, sensorInfoParam?: SensorInfoParam, callback?: Callback<PedometerDetectionResponse>): void
```

取消订阅计步检测器传感器数据。当不再需要接收计步检测器传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。

**起始版本：** 19

**需要权限：** ohos.permission.ACTIVITY_MOTION

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.PEDOMETER_DETECTION | 是 | 传感器类型，该值固定为SensorId.PEDOMETER_DETECTION。 |
| sensorInfoParam | [SensorInfoParam](arkts-sensorservice-sensor-sensorinfoparam-i.md) | 否 | 传感器传入设置参数，可指定deviceId和sensorIndex，用于取消指定设备上指定传感器的订阅。不传入时默认取消本地设备该类型所有传感器的订阅。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PedometerDetectionResponse](arkts-sensorservice-sensor-pedometerdetectionresponse-i.md)&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception;   2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.PedometerDetectionResponse) => {
  console.info(`callback response: ${JSON.stringify(response)}`);
}
// 传感器监听类型
const sensorType = sensor.SensorId.PEDOMETER_DETECTION;
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
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
  // 使用try catch对可能出现的异常进行捕获
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


## off

```TypeScript
function off(type: SensorId.PROXIMITY, callback?: Callback<ProximityResponse>): void
```

取消订阅接近光传感器数据。当不再需要接收接近光传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.PROXIMITY | 是 | 传感器类型，该值固定为SensorId.PROXIMITY。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;ProximityResponse&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;   2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.PROXIMITY, callback1);
  sensor.on(sensor.SensorId.PROXIMITY, callback2);
  // 仅取消callback1的注册
  sensor.off(sensor.SensorId.PROXIMITY, callback1);
  // 取消注册SensorId.PROXIMITY的所有回调
  sensor.off(sensor.SensorId.PROXIMITY);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```


## off

```TypeScript
function off(type: SensorId.PROXIMITY, sensorInfoParam?: SensorInfoParam, callback?: Callback<ProximityResponse>): void
```

取消订阅接近光传感器数据。当不再需要接收接近光传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。

**起始版本：** 19

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.PROXIMITY | 是 | 传感器类型，该值固定为SensorId.PROXIMITY。 |
| sensorInfoParam | [SensorInfoParam](arkts-sensorservice-sensor-sensorinfoparam-i.md) | 否 | 传感器传入设置参数，可指定deviceId和sensorIndex，用于取消指定设备上指定传感器的订阅。不传入时默认取消本地设备该类型所有传感器的订阅。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;ProximityResponse&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception;   2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.ProximityResponse) => {
  console.info(`callback response: ${JSON.stringify(response)}`);
}
// 传感器监听类型
const sensorType = sensor.SensorId.PROXIMITY;
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
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
  // 使用try catch对可能出现的异常进行捕获
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


## off

```TypeScript
function off(type: SensorId.ROTATION_VECTOR, callback?: Callback<RotationVectorResponse>): void
```

取消订阅旋转矢量传感器数据。当不再需要接收旋转矢量传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.ROTATION_VECTOR | 是 | 传感器类型，该值固定为SensorId.ROTATION_VECTOR。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[RotationVectorResponse](arkts-sensorservice-sensor-rotationvectorresponse-i.md)&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;   2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.ROTATION_VECTOR, callback1);
  sensor.on(sensor.SensorId.ROTATION_VECTOR, callback2);
  // 仅取消callback1的注册
  sensor.off(sensor.SensorId.ROTATION_VECTOR, callback1);
  // 取消注册SensorId.ROTATION_VECTOR的所有回调
  sensor.off(sensor.SensorId.ROTATION_VECTOR);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```


## off

```TypeScript
function off(type: SensorId.ROTATION_VECTOR, sensorInfoParam?: SensorInfoParam, callback?: Callback<RotationVectorResponse>): void
```

取消订阅旋转矢量传感器数据。当不再需要接收旋转矢量传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。

**起始版本：** 19

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.ROTATION_VECTOR | 是 | 传感器类型，该值固定为SensorId.ROTATION_VECTOR。 |
| sensorInfoParam | [SensorInfoParam](arkts-sensorservice-sensor-sensorinfoparam-i.md) | 否 | 传感器传入设置参数，可指定deviceId和sensorIndex，用于取消指定设备上指定传感器的订阅。不传入时默认取消本地设备该类型所有传感器的订阅。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[RotationVectorResponse](arkts-sensorservice-sensor-rotationvectorresponse-i.md)&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception;   2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.RotationVectorResponse) => {
  console.info(`callback response: ${JSON.stringify(response)}`);
}
// 传感器监听类型
const sensorType = sensor.SensorId.ROTATION_VECTOR;
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
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
  // 使用try catch对可能出现的异常进行捕获
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


## off

```TypeScript
function off(type: SensorId.SIGNIFICANT_MOTION, callback?: Callback<SignificantMotionResponse>): void
```

取消订阅有效运动传感器数据。当不再需要接收有效运动传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.SIGNIFICANT_MOTION | 是 | 传感器类型，该值固定为SensorId.SIGNIFICANT_MOTION。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SignificantMotionResponse](arkts-sensorservice-sensor-significantmotionresponse-i.md)&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;   2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.SIGNIFICANT_MOTION, callback1);
  sensor.on(sensor.SensorId.SIGNIFICANT_MOTION, callback2);
  // 仅取消callback1的注册
  sensor.off(sensor.SensorId.SIGNIFICANT_MOTION, callback1);
  // 取消注册SensorId.SIGNIFICANT_MOTION的所有回调
  sensor.off(sensor.SensorId.SIGNIFICANT_MOTION);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```


## off

```TypeScript
function off(type: SensorId.SIGNIFICANT_MOTION, sensorInfoParam?: SensorInfoParam, callback?: Callback<SignificantMotionResponse>): void
```

取消订阅有效运动传感器数据。当不再需要接收有效运动传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。

**起始版本：** 19

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.SIGNIFICANT_MOTION | 是 | 传感器类型，该值固定为SensorId.SIGNIFICANT_MOTION。 |
| sensorInfoParam | [SensorInfoParam](arkts-sensorservice-sensor-sensorinfoparam-i.md) | 否 | 传感器传入设置参数，可指定deviceId和sensorIndex，用于取消指定设备上指定传感器的订阅。不传入时默认取消本地设备该类型所有传感器的订阅。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SignificantMotionResponse](arkts-sensorservice-sensor-significantmotionresponse-i.md)&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception;   2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.SignificantMotionResponse) => {
  console.info(`callback response: ${JSON.stringify(response)}`);
}
// 传感器监听类型
const sensorType = sensor.SensorId.SIGNIFICANT_MOTION;
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
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
  // 使用try catch对可能出现的异常进行捕获
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


## off

```TypeScript
function off(type: SensorId.WEAR_DETECTION, callback?: Callback<WearDetectionResponse>): void
```

取消订阅佩戴检测传感器数据。当不再需要接收佩戴检测传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.WEAR_DETECTION | 是 | 传感器类型，该值固定为SensorId.WEAR_DETECTION。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[WearDetectionResponse](arkts-sensorservice-sensor-weardetectionresponse-i.md)&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;   2. Incorrect parameter types; 3. Parameter verification failed. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

function callback1(data: object) {
  console.info('Succeeded in getting callback1 data: ' + JSON.stringify(data));
}

function callback2(data: object) {
  console.info('Succeeded in getting callback2 data: ' + JSON.stringify(data));
}

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.on(sensor.SensorId.WEAR_DETECTION, callback1);
  sensor.on(sensor.SensorId.WEAR_DETECTION, callback2);
  // 仅取消callback1的注册
  sensor.off(sensor.SensorId.WEAR_DETECTION, callback1);
  // 取消注册SensorId.WEAR_DETECTION的所有回调
  sensor.off(sensor.SensorId.WEAR_DETECTION);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke off. Code: ${e.code}, message: ${e.message}`);
}
```


## off

```TypeScript
function off(type: SensorId.FUSION_PRESSURE, sensorInfoParam?: SensorInfoParam, callback?: Callback<FusionPressureResponse>): void
```

取消订阅融合压力传感器数据。当不再需要接收融合压力传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。

**起始版本：** 22

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.FUSION_PRESSURE | 是 | 传感器类型，该值固定为SensorId.FUSION_PRESSURE。 |
| sensorInfoParam | [SensorInfoParam](arkts-sensorservice-sensor-sensorinfoparam-i.md) | 否 | 传感器传入设置参数，可指定deviceId和sensorIndex，用于取消指定设备上指定传感器的订阅。不传入时默认取消本地设备该类型所有传感器的订阅。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[FusionPressureResponse](arkts-sensorservice-sensor-fusionpressureresponse-i.md)&gt; | 否 | 取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;   2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception;   2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.FusionPressureResponse) => {
  console.info(`callback response: ${JSON.stringify(response)}`);
}
// 传感器监听类型
const sensorType = sensor.SensorId.FUSION_PRESSURE;
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
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
  // 使用try catch对可能出现的异常进行捕获
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


## off

```TypeScript
function off(type: SensorId.WEAR_DETECTION, sensorInfoParam?: SensorInfoParam, callback?: Callback<WearDetectionResponse>): void
```

取消订阅佩戴检测传感器数据。当不再需要接收佩戴检测传感器数据时调用此接口取消订阅。off取消订阅必须与on订阅成对出现。

**起始版本：** 19

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorId.WEAR_DETECTION | 是 | 传感器类型，该值固定为SensorId.WEAR_DETECTION。 |
| sensorInfoParam | [SensorInfoParam](arkts-sensorservice-sensor-sensorinfoparam-i.md) | 否 | 传感器传入设置参数，可指定deviceId和sensorIndex，用于取消指定设备上指定传感器的订阅。不传入时默认取消本地设备该类型所有传感器的订阅。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[WearDetectionResponse](arkts-sensorservice-sensor-weardetectionresponse-i.md)&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception;   2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

enum Ret { OK, Failed = -1 }

// 传感器回调
const sensorCallback = (response: sensor.WearDetectionResponse) => {
  console.info(`callback response: ${JSON.stringify(response)}`);
}
// 传感器监听类型
const sensorType = sensor.SensorId.WEAR_DETECTION;
const sensorInfoParam: sensor.SensorInfoParam = { deviceId: -1, sensorIndex: 0 };

function sensorSubscribe(): Ret {
  let ret: Ret = Ret.OK;
  // 使用try catch对可能出现的异常进行捕获
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
  // 使用try catch对可能出现的异常进行捕获
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


## off

```TypeScript
function off(type: SensorType.SENSOR_TYPE_ID_ACCELEROMETER, callback?: Callback<AccelerometerResponse>): void
```

取消订阅加速度传感器数据。off取消订阅必须与on订阅成对出现。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.ACCELEROMETER]
> off
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [off](#off)(type: SensorId.ACCELEROMETER, callback?: Callback&lt;AccelerometerResponse&gt;)

**需要权限：** ohos.permission.ACCELEROMETER

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_ACCELEROMETER | 是 | 要取消订阅的加速度传感器类型为SENSOR_TYPE_ID_ACCELEROMETER。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;AccelerometerResponse&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.AccelerometerResponse) {
  console.info('Succeeded in invoking off. X-coordinate component: ' + data.x);
  console.info('Succeeded in invoking off. Y-coordinate component: ' + data.y);
  console.info('Succeeded in invoking off. Z-coordinate component: ' + data.z);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_ACCELEROMETER, callback);
```


## off

```TypeScript
function off(type: SensorType.SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED,
    callback?: Callback<AccelerometerUncalibratedResponse>): void
```

取消订阅未校准加速度传感器数据。off取消订阅必须与on订阅成对出现。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.ACCELEROMETER_UNCALIBRATED]
> off
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [off](#off)(type: SensorId.ACCELEROMETER_UNCALIBRATED, callback?: Callback&lt;AccelerometerUncalibratedResponse&gt;)

**需要权限：** ohos.permission.ACCELEROMETER

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED | 是 | 要取消订阅的未校准加速度计传感器类型为SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AccelerometerUncalibratedResponse](arkts-sensorservice-sensor-accelerometeruncalibratedresponse-i.md)&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.AccelerometerUncalibratedResponse) {
  console.info('Succeeded in invoking off. X-coordinate component: ' + data.x);
  console.info('Succeeded in invoking off. Y-coordinate component: ' + data.y);
  console.info('Succeeded in invoking off. Z-coordinate component: ' + data.z);
  console.info('Succeeded in invoking off. X-coordinate bias: ' + data.biasX);
  console.info('Succeeded in invoking off. Y-coordinate bias: ' + data.biasY);
  console.info('Succeeded in invoking off. Z-coordinate bias: ' + data.biasZ);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_ACCELEROMETER_UNCALIBRATED, callback);
```


## off

```TypeScript
function off(type: SensorType.SENSOR_TYPE_ID_AMBIENT_LIGHT, callback?: Callback<LightResponse>): void
```

取消订阅环境光传感器数据。off取消订阅必须与on订阅成对出现。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.AMBIENT_LIGHT]
> off
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [off](#off)(type: SensorId.AMBIENT_LIGHT, callback?: Callback&lt;LightResponse&gt;)

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_AMBIENT_LIGHT | 是 | 要取消订阅的环境光传感器类型为SENSOR_TYPE_ID_AMBIENT_LIGHT。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;LightResponse&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.LightResponse) {
  console.info('Succeeded in invoking off. Illumination: ' + data.intensity);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_AMBIENT_LIGHT, callback);
```


## off

```TypeScript
function off(type: SensorType.SENSOR_TYPE_ID_AMBIENT_TEMPERATURE, callback?: Callback<AmbientTemperatureResponse>): void
```

取消订阅环境温度传感器数据。off取消订阅必须与on订阅成对出现。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.AMBIENT_TEMPERATURE]
> off
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [off](#off)(type: SensorId.AMBIENT_TEMPERATURE, callback?: Callback&lt;AmbientTemperatureResponse&gt;)

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_AMBIENT_TEMPERATURE | 是 | 要取消订阅的环境温度传感器类型为SENSOR_TYPE_ID_AMBIENT_TEMPERATURE。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[AmbientTemperatureResponse](arkts-sensorservice-sensor-ambienttemperatureresponse-i.md)&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.AmbientTemperatureResponse) {
  console.info('Succeeded in invoking off. Temperature: ' + data.temperature);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_AMBIENT_TEMPERATURE, callback);
```


## off

```TypeScript
function off(type: SensorType.SENSOR_TYPE_ID_BAROMETER, callback?: Callback<BarometerResponse>): void
```

取消订阅气压计传感器数据。off取消订阅必须与on订阅成对出现。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.BAROMETER]
> off
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [off](#off)(type: SensorId.BAROMETER, callback?: Callback&lt;BarometerResponse&gt;)

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_BAROMETER | 是 | 要取消订阅的气压计传感器类型为SENSOR_TYPE_ID_BAROMETER。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;BarometerResponse&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.BarometerResponse) {
  console.info('Succeeded in invoking off. Atmospheric pressure: ' + data.pressure);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_BAROMETER, callback);
```


## off

```TypeScript
function off(type: SensorType.SENSOR_TYPE_ID_GRAVITY, callback?: Callback<GravityResponse>): void
```

取消订阅重力传感器数据。off取消订阅必须与on订阅成对出现。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.GRAVITY]
> off
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [off](#off)(type: SensorId.GRAVITY, callback?: Callback&lt;GravityResponse&gt;)

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_GRAVITY | 是 | 要取消订阅的重力传感器类型为SENSOR_TYPE_ID_GRAVITY。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[GravityResponse](arkts-sensorservice-sensor-gravityresponse-i.md)&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.GravityResponse) {
  console.info('Succeeded in invoking off. X-coordinate component: ' + data.x);
  console.info('Succeeded in invoking off. Y-coordinate component: ' + data.y);
  console.info('Succeeded in invoking off. Z-coordinate component: ' + data.z);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_GRAVITY, callback);
```


## off

```TypeScript
function off(type: SensorType.SENSOR_TYPE_ID_GYROSCOPE, callback?: Callback<GyroscopeResponse>): void
```

取消订阅陀螺仪传感器数据。off取消订阅必须与on订阅成对出现。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.GYROSCOPE]
> off
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [off](#off)(type: SensorId.GYROSCOPE, callback?: Callback&lt;GyroscopeResponse&gt;)

**需要权限：** ohos.permission.GYROSCOPE

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_GYROSCOPE | 是 | 要取消订阅的陀螺仪传感器类型为SENSOR_TYPE_ID_GYROSCOPE。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;GyroscopeResponse&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.GyroscopeResponse) {
  console.info('Succeeded in invoking off. X-coordinate component: ' + data.x);
  console.info('Succeeded in invoking off. Y-coordinate component: ' + data.y);
  console.info('Succeeded in invoking off. Z-coordinate component: ' + data.z);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_GYROSCOPE, callback);
```


## off

```TypeScript
function off(type: SensorType.SENSOR_TYPE_ID_GYROSCOPE_UNCALIBRATED, callback?: Callback<GyroscopeUncalibratedResponse>): void
```

取消订阅未校准陀螺仪传感器数据。off取消订阅必须与on订阅成对出现。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.GYROSCOPE_UNCALIBRATED]
> off
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [off](#off)(type: SensorId.GYROSCOPE_UNCALIBRATED, callback?: Callback&lt;GyroscopeUncalibratedResponse&gt;)

**需要权限：** ohos.permission.GYROSCOPE

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_GYROSCOPE_UNCALIBRATED | 是 | 要取消订阅的未校准陀螺仪传感器类型为SENSOR_TYPE_ID_GYROSCOPE_UNCALIBRATED。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[GyroscopeUncalibratedResponse](arkts-sensorservice-sensor-gyroscopeuncalibratedresponse-i.md)&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.GyroscopeUncalibratedResponse) {
  console.info('Succeeded in invoking off. X-coordinate component: ' + data.x);
  console.info('Succeeded in invoking off. Y-coordinate component: ' + data.y);
  console.info('Succeeded in invoking off. Z-coordinate component: ' + data.z);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_GYROSCOPE_UNCALIBRATED, callback);
```


## off

```TypeScript
function off(type: SensorType.SENSOR_TYPE_ID_HALL, callback?: Callback<HallResponse>): void
```

取消订阅霍尔传感器数据。off取消订阅必须与on订阅成对出现。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.HALL]
> off
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [off](#off)(type: SensorId.HALL, callback?: Callback&lt;HallResponse&gt;)

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_HALL | 是 | 要取消订阅的霍尔传感器类型为SENSOR_TYPE_ID_HALL。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[HallResponse](arkts-sensorservice-sensor-hallresponse-i.md)&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.HallResponse) {
  console.info('Succeeded in invoking off. Status: ' + data.status);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_HALL, callback);
```


## off

```TypeScript
function off(type: SensorType.SENSOR_TYPE_ID_HEART_RATE, callback?: Callback<HeartRateResponse>): void
```

取消订阅心率传感器数据。off取消订阅必须与on订阅成对出现。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.HEART_RATE]
> off
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [off](#off)(type: SensorId.HEART_RATE, callback?: Callback&lt;HeartRateResponse&gt;)

**需要权限：** ohos.permission.HEALTH_DATA

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_HEART_RATE | 是 | 要取消订阅的心率传感器类型为SENSOR_TYPE_ID_HEART_RATE。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;HeartRateResponse&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.HeartRateResponse) {
  console.info('Succeeded in invoking off. Heart rate: ' + data.heartRate);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_HEART_RATE, callback);
```


## off

```TypeScript
function off(type: SensorType.SENSOR_TYPE_ID_HUMIDITY, callback?: Callback<HumidityResponse>): void
```

取消订阅湿度传感器数据。off取消订阅必须与on订阅成对出现。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.HUMIDITY]
> off
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [off](#off)(type: SensorId.HUMIDITY, callback?: Callback&lt;HumidityResponse&gt;)

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_HUMIDITY | 是 | 要取消订阅的湿度传感器类型为SENSOR_TYPE_ID_HUMIDITY。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[HumidityResponse](arkts-sensorservice-sensor-humidityresponse-i.md)&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.HumidityResponse) {
  console.info('Succeeded in invoking off. Humidity: ' + data.humidity);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_HUMIDITY, callback);
```


## off

```TypeScript
function off(type: SensorType.SENSOR_TYPE_ID_LINEAR_ACCELERATION, callback?: Callback<LinearAccelerometerResponse>): void
```

取消订阅线性加速度传感器数据。off取消订阅必须与on订阅成对出现。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.LINEAR_ACCELEROMETER]
> off
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [off](#off)(type: SensorId.LINEAR_ACCELEROMETER, callback?: Callback&lt;LinearAccelerometerResponse&gt;)

**需要权限：** ohos.permission.ACCELEROMETER

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_LINEAR_ACCELERATION | 是 | 要取消订阅的线性加速度传感器类型为SENSOR_TYPE_ID_LINEAR_ACCELERATION。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[LinearAccelerometerResponse](arkts-sensorservice-sensor-linearaccelerometerresponse-i.md)&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.LinearAccelerometerResponse) {
  console.info('Succeeded in invoking off. X-coordinate component: ' + data.x);
  console.info('Succeeded in invoking off. Y-coordinate component: ' + data.y);
  console.info('Succeeded in invoking off. Z-coordinate component: ' + data.z);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_LINEAR_ACCELERATION, callback);
```


## off

```TypeScript
function off(type: SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD, callback?: Callback<MagneticFieldResponse>): void
```

取消订阅磁场传感器数据。off取消订阅必须与on订阅成对出现。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.MAGNETIC_FIELD]
> off
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [off](#off)(type: SensorId.MAGNETIC_FIELD, callback?: Callback&lt;MagneticFieldResponse&gt;)

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD | 是 | 要取消订阅的磁场传感器类型为SENSOR_TYPE_ID_MAGNETIC_FIELD。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[MagneticFieldResponse](arkts-sensorservice-sensor-magneticfieldresponse-i.md)&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.MagneticFieldResponse) {
  console.info('Succeeded in invoking off. X-coordinate component: ' + data.x);
  console.info('Succeeded in invoking off. Y-coordinate component: ' + data.y);
  console.info('Succeeded in invoking off. Z-coordinate component: ' + data.z);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD, callback);
```


## off

```TypeScript
function off(type: SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED, callback?: Callback<MagneticFieldUncalibratedResponse>): void
```

取消订阅未校准磁场传感器数据。off取消订阅必须与on订阅成对出现。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.MAGNETIC_FIELD_UNCALIBRATED]
> off
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [off](#off)(type: SensorId.MAGNETIC_FIELD_UNCALIBRATED, callback?: Callback&lt;MagneticFieldUncalibratedResponse&gt;)

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED | 是 | 要取消订阅的未校准磁场传感器类型为SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[MagneticFieldUncalibratedResponse](arkts-sensorservice-sensor-magneticfielduncalibratedresponse-i.md)&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.MagneticFieldUncalibratedResponse) {
  console.info('Succeeded in invoking off. X-coordinate component: ' + data.x);
  console.info('Succeeded in invoking off. Y-coordinate component: ' + data.y);
  console.info('Succeeded in invoking off. Z-coordinate component: ' + data.z);
  console.info('Succeeded in invoking off. X-coordinate bias: ' + data.biasX);
  console.info('Succeeded in invoking off. Y-coordinate bias: ' + data.biasY);
  console.info('Succeeded in invoking off. Z-coordinate bias: ' + data.biasZ);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_MAGNETIC_FIELD_UNCALIBRATED, callback);
```


## off

```TypeScript
function off(type: SensorType.SENSOR_TYPE_ID_ORIENTATION, callback?: Callback<OrientationResponse>): void
```

取消订阅方向传感器数据。off取消订阅必须与on订阅成对出现。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.ORIENTATION]
> off
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [off](#off)(type: SensorId.ORIENTATION, callback?: Callback&lt;OrientationResponse&gt;)

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_ORIENTATION | 是 | 要取消订阅的方向传感器类型为SENSOR_TYPE_ID_ORIENTATION。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[OrientationResponse](arkts-sensorservice-sensor-orientationresponse-i.md)&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.OrientationResponse) {
  console.info('Succeeded in invoking off. The device rotates at an angle around the X axis: ' + data.beta);
  console.info('Succeeded in invoking off. The device rotates at an angle around the Y axis: ' + data.gamma);
  console.info('Succeeded in invoking off. The device rotates at an angle around the Z axis: ' + data.alpha);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_ORIENTATION, callback);
```


## off

```TypeScript
function off(type: SensorType.SENSOR_TYPE_ID_PEDOMETER, callback?: Callback<PedometerResponse>): void
```

取消订阅计步传感器数据。off取消订阅必须与on订阅成对出现。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.PEDOMETER]
> off
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [off](#off)(type: SensorId.PEDOMETER, callback?: Callback&lt;PedometerResponse&gt;)

**需要权限：** ohos.permission.ACTIVITY_MOTION

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_PEDOMETER | 是 | 要取消订阅的计步传感器类型为SENSOR_TYPE_ID_PEDOMETER。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PedometerResponse](arkts-sensorservice-sensor-pedometerresponse-i.md)&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.PedometerResponse) {
  console.info('Succeeded in invoking off. Steps: ' + data.steps);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_PEDOMETER, callback);
```


## off

```TypeScript
function off(type: SensorType.SENSOR_TYPE_ID_PEDOMETER_DETECTION, callback?: Callback<PedometerDetectionResponse>): void
```

取消订阅计步检测传感器数据。off取消订阅必须与on订阅成对出现。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.PEDOMETER_DETECTION]
> off
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [off](#off)(type: SensorId.PEDOMETER_DETECTION, callback?: Callback&lt;PedometerDetectionResponse&gt;)

**需要权限：** ohos.permission.ACTIVITY_MOTION

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_PEDOMETER_DETECTION | 是 | 要取消订阅的计步检测传感器类型为SENSOR_TYPE_ID_PEDOMETER_DETECTION。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[PedometerDetectionResponse](arkts-sensorservice-sensor-pedometerdetectionresponse-i.md)&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.PedometerDetectionResponse) {
  console.info('Succeeded in invoking off. Scalar data: ' + data.scalar);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_PEDOMETER_DETECTION, callback);
```


## off

```TypeScript
function off(type: SensorType.SENSOR_TYPE_ID_PROXIMITY, callback?: Callback<ProximityResponse>): void
```

取消订阅接近光传感器数据。off取消订阅必须与on订阅成对出现。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.PROXIMITY]
> off
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [off](#off)(type: SensorId.PROXIMITY, callback?: Callback&lt;ProximityResponse&gt;)

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_PROXIMITY | 是 | 要取消订阅的接近光传感器类型为SENSOR_TYPE_ID_PROXIMITY。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;ProximityResponse&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.ProximityResponse) {
  console.info('Succeeded in invoking off. Distance: ' + data.distance);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_PROXIMITY, callback);
```


## off

```TypeScript
function off(type: SensorType.SENSOR_TYPE_ID_ROTATION_VECTOR, callback?: Callback<RotationVectorResponse>): void
```

取消订阅旋转矢量传感器数据。off取消订阅必须与on订阅成对出现。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.ROTATION_VECTOR]
> off
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [off](#off)(type: SensorId.ROTATION_VECTOR, callback?: Callback&lt;RotationVectorResponse&gt;)

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_ROTATION_VECTOR | 是 | 要取消订阅的旋转矢量传感器类型为SENSOR_TYPE_ID_ROTATION_VECTOR。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[RotationVectorResponse](arkts-sensorservice-sensor-rotationvectorresponse-i.md)&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.RotationVectorResponse) {
  console.info('Succeeded in invoking off. X-coordinate component: ' + data.x);
  console.info('Succeeded in invoking off. Y-coordinate component: ' + data.y);
  console.info('Succeeded in invoking off. Z-coordinate component: ' + data.z);
  console.info('Succeeded in invoking off. Scalar quantity: ' + data.w);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_ROTATION_VECTOR, callback);
```


## off

```TypeScript
function off(type: SensorType.SENSOR_TYPE_ID_SIGNIFICANT_MOTION, callback?: Callback<SignificantMotionResponse>): void
```

取消订阅有效运动传感器数据。off取消订阅必须与on订阅成对出现。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.SIGNIFICANT_MOTION]
> off
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [off](#off)(type: SensorId.SIGNIFICANT_MOTION, callback?: Callback&lt;SignificantMotionResponse&gt;)

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_SIGNIFICANT_MOTION | 是 | 要取消订阅的有效运动传感器类型为SENSOR_TYPE_ID_SIGNIFICANT_MOTION。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SignificantMotionResponse](arkts-sensorservice-sensor-significantmotionresponse-i.md)&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

function callback(data: sensor.SignificantMotionResponse) {
  console.info('Succeeded in invoking off. Scalar data: ' + data.scalar);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_SIGNIFICANT_MOTION, callback);
```


## off

```TypeScript
function off(type: SensorType.SENSOR_TYPE_ID_WEAR_DETECTION, callback?: Callback<WearDetectionResponse>): void
```

取消订阅佩戴检测传感器数据。off取消订阅必须与on订阅成对出现。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用[sensor.on.WEAR_DETECTION]
> off
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [off](#off)(type: SensorId.WEAR_DETECTION, callback?: Callback&lt;WearDetectionResponse&gt;)

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | SensorType.SENSOR_TYPE_ID_WEAR_DETECTION | 是 | 要取消订阅的佩戴检测传感器类型为SENSOR_TYPE_ID_WEAR_DETECTION。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[WearDetectionResponse](arkts-sensorservice-sensor-weardetectionresponse-i.md)&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';

function accCallback(data: sensor.WearDetectionResponse) {
  console.info('Succeeded in invoking off. Wear status: ' + data.value);
}

sensor.off(sensor.SensorType.SENSOR_TYPE_ID_WEAR_DETECTION, accCallback);
```


## off('sensorStatusChange')

```TypeScript
function off(type: 'sensorStatusChange', callback?: Callback<SensorStatusEvent>): void
```

取消监听传感器上线下线状态的变化。当不再需要感知传感器上下线状态时调用此接口取消监听。off取消监听必须与on监听成对出现。

**起始版本：** 19

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'sensorStatusChange' | 是 | 固定传入'sensorStatusChange'，状态监听固定参数。 |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SensorStatusEvent](arkts-sensorservice-sensor-sensorstatusevent-i.md)&gt; | 否 | 回调函数，需要取消订阅的回调函数，若无此参数，则取消订阅当前类型的所有回调函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception;   2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

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
  sensor.on('sensorStatusChange', statusChangeCallback);
  sensor.on('sensorStatusChange', statusChangeCallback2);
  
  // 3秒后注销第一个监听
  setTimeout(() => {
    sensor.off('sensorStatusChange', statusChangeCallback);
  }, 3000);
  // 5秒后注销所有监听
  setTimeout(() => {
    sensor.off('sensorStatusChange');
  }, 5000);
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to invoke on. Code: ${e.code}, message: ${e.message}`);
}
```
