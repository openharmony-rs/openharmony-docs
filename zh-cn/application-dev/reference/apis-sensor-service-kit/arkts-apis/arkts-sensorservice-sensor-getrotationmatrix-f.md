# getRotationMatrix

## 导入模块

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## getRotationMatrix

```TypeScript
function getRotationMatrix(rotationVector: Array<double>, callback: AsyncCallback<Array<double>>): void
```

根据旋转矢量获取旋转矩阵。使用callback异步回调。

**起始版本：** 23

<!--Device-sensor-function getRotationMatrix(rotationVector: Array<double>, callback: AsyncCallback<Array<double>>): void--><!--Device-sensor-function getRotationMatrix(rotationVector: Array<double>, callback: AsyncCallback<Array<double>>): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rotationVector | Array&lt;double&gt; | 是 | 旋转矢量。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Array&lt;double&gt;&gt; | 是 | 回调函数，异步返回3*3旋转矩阵。 |

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
  let rotationVector = [0.20046076, 0.21907, 0.73978853, 0.60376877];
  sensor.getRotationMatrix(rotationVector, (err: BusinessError, data: Array<number>) => {
    if (err) {
      console.error(`Failed to get rotationMatrix. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    for (let i = 0; i < data.length; i++) {
      console.info('Succeeded in getting data[' + i + ']: ' + data[i]);
    }
  })
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get rotationMatrix. Code: ${e.code}, message: ${e.message}`);
}
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  let rotationVector = [0.20046076, 0.21907, 0.73978853, 0.60376877];
  sensor.getRotationMatrix(rotationVector, (err: BusinessError<void> | null, data: Array<double> | undefined) => {
    if (err) {
      console.error(`Failed to get rotationMatrix. Code: ${err?.code}, message: ${err?.message}`);
      return;
    }
    console.info('Succeeded getting rotationMatrix: ' + JSON.stringify(data));
  })
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get rotationMatrix. Code: ${e.code}, message: ${e.message}`);
}
```


## getRotationMatrix

```TypeScript
function getRotationMatrix(rotationVector: Array<double>): Promise<Array<double>>
```

根据旋转矢量获取旋转矩阵。使用Promise异步回调。

**起始版本：** 23

<!--Device-sensor-function getRotationMatrix(rotationVector: Array<double>): Promise<Array<double>>--><!--Device-sensor-function getRotationMatrix(rotationVector: Array<double>): Promise<Array<double>>-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rotationVector | Array&lt;double&gt; | 是 | 旋转矢量。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;double&gt;&gt; | Promise对象，使用异步方式返回旋转矩阵。 |

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
  let rotationVector = [0.20046076, 0.21907, 0.73978853, 0.60376877];
  const promise = sensor.getRotationMatrix(rotationVector);
  promise.then((data: Array<number>) => {
    for (let i = 0; i < data.length; i++) {
      console.info('Succeeded in getting data[' + i + ']: ' + data[i]);
    }
  }, (err: BusinessError) => {
    console.error(`Failed to get rotationMatrix. Code: ${err.code}, message: ${err.message}`);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get rotationMatrix. Code: ${e.code}, message: ${e.message}`);
}
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  let rotationVector = [0.20046076, 0.21907, 0.73978853, 0.60376877];
  const promise = sensor.getRotationMatrix(rotationVector);
  promise.then((data) => {
    console.info('Succeeded getting rotationMatrix: ' + JSON.stringify(data));
  }, (err) => {
    console.error(`Failed to get rotationMatrix. Code: ${err.code}, message: ${err.message}`);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get rotationMatrix. Code: ${e.code}, message: ${e.message}`);
}
```


## getRotationMatrix

```TypeScript
function getRotationMatrix(gravity: Array<double>, geomagnetic: Array<double>, callback: AsyncCallback<RotationMatrixResponse>): void
```

根据重力矢量和地磁矢量计算旋转矩阵。使用callback异步回调。

**起始版本：** 23

<!--Device-sensor-function getRotationMatrix(gravity: Array<double>, geomagnetic: Array<double>, callback: AsyncCallback<RotationMatrixResponse>): void--><!--Device-sensor-function getRotationMatrix(gravity: Array<double>, geomagnetic: Array<double>, callback: AsyncCallback<RotationMatrixResponse>): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| gravity | Array&lt;double&gt; | 是 | 重力矢量。 |
| geomagnetic | Array&lt;double&gt; | 是 | 地磁矢量。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[RotationMatrixResponse](arkts-sensorservice-sensor-rotationmatrixresponse-i.md)&gt; | 是 | 回调函数，异步返回旋转矩阵。 |

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
  let gravity = [-0.27775216, 0.5351276, 9.788099];
  let geomagnetic = [210.87253, -78.6096, -111.44444];
  sensor.getRotationMatrix(gravity, geomagnetic, (err: BusinessError, data: sensor.RotationMatrixResponse) => {
    if (err) {
      console.error(`Failed to get rotationMatrix. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in getting rotationMatrix' + JSON.stringify(data));
  })
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get rotationMatrix. Code: ${e.code}, message: ${e.message}`);
}
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  let gravity: double[] = [-0.27775216, 0.5351276, 9.788099];
  let geomagnetic: double[] = [210.87253, -78.6096, -111.44444];
  sensor.getRotationMatrix(gravity, geomagnetic, (err: BusinessError<void> | null, data: sensor.RotationMatrixResponse | undefined) => {
    if (err) {
      console.error(`Failed to get rotationMatrix. Code: ${err?.code}, message: ${err?.message}`);
      return;
    }
    console.info('Succeeded in getting rotationMatrix' + JSON.stringify(data));
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get rotationMatrix. Code: ${e.code}, message: ${e.message}`);
}
```


## getRotationMatrix

```TypeScript
function getRotationMatrix(gravity: Array<double>, geomagnetic: Array<double>): Promise<RotationMatrixResponse>
```

根据重力矢量和地磁矢量计算旋转矩阵。使用Promise异步回调。

**起始版本：** 23

<!--Device-sensor-function getRotationMatrix(gravity: Array<double>, geomagnetic: Array<double>): Promise<RotationMatrixResponse>--><!--Device-sensor-function getRotationMatrix(gravity: Array<double>, geomagnetic: Array<double>): Promise<RotationMatrixResponse>-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| gravity | Array&lt;double&gt; | 是 | 重力向量。 |
| geomagnetic | Array&lt;double&gt; | 是 | 地磁矢量。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[RotationMatrixResponse](arkts-sensorservice-sensor-rotationmatrixresponse-i.md)&gt; | Promise对象，使用异步方式返回旋转矩阵。RotationMatrixResponse对象包含设备的旋转矩阵和倾斜矩阵，可用于计算设备的姿态和方向 信息。 |

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
  let gravity = [-0.27775216, 0.5351276, 9.788099];
  let geomagnetic = [210.87253, -78.6096, -111.44444];
  const promise = sensor.getRotationMatrix(gravity, geomagnetic);
  promise.then((data: sensor.RotationMatrixResponse) => {
    console.info('Succeeded in getting rotationMatrix' + JSON.stringify(data));
  }, (err: BusinessError) => {
    console.error(`Failed to get rotationMatrix. Code: ${err.code}, message: ${err.message}`);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get rotationMatrix. Code: ${e.code}, message: ${e.message}`);
}
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  let gravity = [-0.27775216, 0.5351276, 9.788099];
  let geomagnetic = [210.87253, -78.6096, -111.44444];
  const promise = sensor.getRotationMatrix(gravity, geomagnetic);
  promise.then((data) => {
    console.info('Succeeded in getting rotationMatrix' + JSON.stringify(data));
  }, (err) => {
    console.error(`Failed to get rotationMatrix. Code: ${err.code}, message: ${err.message}`);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get rotationMatrix. Code: ${e.code}, message: ${e.message}`);
}
```

