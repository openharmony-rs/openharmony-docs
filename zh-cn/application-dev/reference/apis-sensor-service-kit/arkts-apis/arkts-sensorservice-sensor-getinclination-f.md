# getInclination

## 导入模块

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## getInclination

```TypeScript
function getInclination(inclinationMatrix: Array<double>, callback: AsyncCallback<double>): void
```

根据倾斜矩阵计算地磁倾角。使用callback异步回调。

**起始版本：** 23

<!--Device-sensor-function getInclination(inclinationMatrix: Array<double>, callback: AsyncCallback<double>): void--><!--Device-sensor-function getInclination(inclinationMatrix: Array<double>, callback: AsyncCallback<double>): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| inclinationMatrix | Array&lt;double&gt; | 是 | 倾斜矩阵。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;double&gt; | 是 | 回调函数，异步返回地磁倾角，单位：rad（弧度）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception; <br> 2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  // inclinationMatrix可以为3*3，或者4*4
  let inclinationMatrix = [
    1, 0, 0,
    0, 1, 0,
    0, 0, 1
  ]
  sensor.getInclination(inclinationMatrix, (err, data) => {
    let error = err as BusinessError;
    let dataValue = data as number;
    if (error) {
      console.error(`Failed to get inclination. Code: ${error.code}, message: ${error.message}`);
      return;
    }
    console.info('Succeeded in getting inclination: ' + dataValue);
  })
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get inclination. Code: ${e.code}, message: ${e.message}`);
}
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  // inclinationMatrix可以为3*3，或者4*4
  let inclinationMatrix = [
    1, 0, 0,
    0, 1, 0,
    0, 0, 1
  ]
  sensor.getInclination(inclinationMatrix, (err, data) => {
    let error = err as BusinessError;
    let dataValue = data as double;
    if (error) {
      console.error(`Failed to get inclination. Code: ${error.code}, message: ${error.message}`);
      return;
    }
    console.info('Succeeded in getting inclination: ' + dataValue);
  })
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get inclination. Code: ${e.code}, message: ${e.message}`);
}
```


## getInclination

```TypeScript
function getInclination(inclinationMatrix: Array<double>): Promise<double>
```

根据倾斜矩阵计算地磁倾角。使用Promise异步回调。

**起始版本：** 23

<!--Device-sensor-function getInclination(inclinationMatrix: Array<double>): Promise<double>--><!--Device-sensor-function getInclination(inclinationMatrix: Array<double>): Promise<double>-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| inclinationMatrix | Array&lt;double&gt; | 是 | 倾斜矩阵。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;double&gt; | Promise对象，使用异步方式返回地磁倾斜角，单位：rad（弧度）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception; <br> 2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  // inclinationMatrix可以为3*3，或者4*4
  let inclinationMatrix = [
    1, 0, 0,
    0, 1, 0,
    0, 0, 1
  ]
  const promise = sensor.getInclination(inclinationMatrix);
  promise.then((data: number) => {
    console.info('Succeeded in getting inclination: ' + data);
  }, (err: BusinessError) => {
    console.error(`Failed to get inclination. Code: ${err.code}, message: ${err.message}`);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get inclination. Code: ${e.code}, message: ${e.message}`);
}
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  // inclinationMatrix可以为3*3，或者4*4
  let inclinationMatrix = [
    1, 0, 0,
    0, 1, 0,
    0, 0, 1
  ]
  const promise = sensor.getInclination(inclinationMatrix);
  promise.then((data: double) => {
    console.info('Succeeded in getting inclination: ' + data);
  }, (err: BusinessError) => {
    console.error(`Failed to get inclination. Code: ${err.code}, message: ${err.message}`);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get inclination. Code: ${e.code}, message: ${e.message}`);
}
```

