# getQuaternion

## getQuaternion

```TypeScript
function getQuaternion(rotationVector: Array<double>, callback: AsyncCallback<Array<double>>): void
```

根据旋转向量计算归一化四元数，使用Callback异步方式返回结果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-sensor-function getQuaternion(rotationVector: Array<double>, callback: AsyncCallback<Array<double>>): void--><!--Device-sensor-function getQuaternion(rotationVector: Array<double>, callback: AsyncCallback<Array<double>>): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rotationVector | Array&lt;double&gt; | 是 | 旋转矢量。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Array&lt;double&gt;&gt; | 是 | 回调函数，异步返回归一化四元数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception; &lt;br&gt; 2. Sensor service ipc exception;3. Sensor data channel exception. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  let rotationVector = [0.20046076, 0.21907, 0.73978853, 0.60376877];
  sensor.getQuaternion(rotationVector, (err, data) => {
    let error = err as BusinessError;
    let dataValue = data as Array<number>;
    if (error) {
      console.error(`Failed to get quaternion. Code: ${error.code}, message: ${error.message}`);
      return;
    }
    for (let i = 0; i < dataValue.length; i++) {
      console.info('Succeeded in getting data[' + i + ']: ' + dataValue[i]);
    }
  })
} catch (error: Error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get quaternion. Code: ${e.code}, message: ${e.message}`);
}
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  let rotationVector = [0.20046076, 0.21907, 0.73978853, 0.60376877];
  sensor.getQuaternion(rotationVector, (err, data) => {
    let error = err as BusinessError;
    let dataValue = data as Array<double>;
    if (error) {
      console.error(`Failed to get quaternion. Code: ${error.code}, message: ${error.message}`);
      return;
    }
    for (let i = 0; i < dataValue.length; i++) {
      console.info('Succeeded in getting data[' + i + ']: ' + dataValue[i]);
    }
  })
} catch (error: Error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get quaternion. Code: ${e.code}, message: ${e.message}`);
}
```


## getQuaternion

```TypeScript
function getQuaternion(rotationVector: Array<double>): Promise<Array<double>>
```

根据旋转向量计算归一化四元数，使用Promise异步方式返回结果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-sensor-function getQuaternion(rotationVector: Array<double>): Promise<Array<double>>--><!--Device-sensor-function getQuaternion(rotationVector: Array<double>): Promise<Array<double>>-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rotationVector | Array&lt;double&gt; | 是 | 旋转矢量。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;double&gt;&gt; | Promise对象，使用异步方式返回归一化四元数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception; &lt;br&gt; 2. Sensor service ipc exception;3. Sensor data channel exception. |

## 示例

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  let rotationVector = [0.20046076, 0.21907, 0.73978853, 0.60376877];
  const promise = sensor.getQuaternion(rotationVector);
  promise.then((data: Array<number>) => {
    for (let i = 0; i < data.length; i++) {
      console.info('Succeeded in getting data[' + i + ']: ' + data[i]);
    }
  }, (err: BusinessError) => {
    console.error(`Failed to get quaternion. Code: ${err.code}, message: ${err.message}`);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get quaternion. Code: ${e.code}, message: ${e.message}`);
}
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  let rotationVector = [0.20046076, 0.21907, 0.73978853, 0.60376877];
  const promise = sensor.getQuaternion(rotationVector);
  promise.then((data: Array<double>) => {
    for (let i = 0; i < data.length; i++) {
      console.info('Succeeded in getting data[' + i + ']: ' + data[i]);
    }
  }, (err: BusinessError) => {
    console.error(`Failed to get quaternion. Code: ${err.code}, message: ${err.message}`);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get quaternion. Code: ${e.code}, message: ${e.message}`);
}
```

