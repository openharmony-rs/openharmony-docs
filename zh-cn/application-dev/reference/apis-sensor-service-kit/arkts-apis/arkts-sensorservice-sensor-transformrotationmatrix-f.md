# transformRotationMatrix

## transformRotationMatrix

```TypeScript
function transformRotationMatrix(inRotationVector: Array<double>, coordinates: CoordinatesOptions,
    callback: AsyncCallback<Array<double>>): void
```

根据指定坐标系映射旋转矩阵，使用Callback异步方式返回结果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-sensor-function transformRotationMatrix(inRotationVector: Array<double>, coordinates: CoordinatesOptions,    callback: AsyncCallback<Array<double>>): void--><!--Device-sensor-function transformRotationMatrix(inRotationVector: Array<double>, coordinates: CoordinatesOptions,    callback: AsyncCallback<Array<double>>): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| inRotationVector | Array&lt;double&gt; | 是 | 旋转矩阵。 |
| coordinates | [CoordinatesOptions](arkts-sensorservice-sensor-coordinatesoptions-i.md) | 是 | 指定坐标系方向。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Array&lt;double&gt;&gt; | 是 | 回调函数，异步返回映射后的旋转矩阵。 |

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
  let rotationMatrix = [
    1, 0, 0,
    0, 0.87, -0.50,
    0, 0.50, 0.87
  ];
  sensor.transformRotationMatrix(rotationMatrix, { x: 1, y: 3 }, (err, data) => {
    let error = err as BusinessError;
    let dataValue = data as Array<number>;
    if (error) {
      console.error(`Failed to transform rotationMatrix. Code: ${error.code}, message: ${error.message}`);
      return;
    }
    for (let i = 0; i < dataValue.length; i++) {
      console.info('Succeeded in getting data[' + i + '] = ' + dataValue[i]);
    }
  })
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to transform rotationMatrix. Code: ${e.code}, message: ${e.message}`);
}
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  let rotationMatrix = [
    1, 0, 0,
    0, 0.87, -0.50,
    0, 0.50, 0.87
  ];
  sensor.transformRotationMatrix(rotationMatrix, { x: 1, y: 3 }, (err, data) => {
    let error = err as BusinessError;
    let dataValue = data as Array<double>;
    if (error) {
      console.error(`Failed to transform rotationMatrix. Code: ${error.code}, message: ${error.message}`);
      return;
    }
    for (let i = 0; i < dataValue.length; i++) {
      console.info('Succeeded in getting data[' + i + '] = ' + dataValue[i]);
    }
  })
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to transform rotationMatrix. Code: ${e.code}, message: ${e.message}`);
}
```


## transformRotationMatrix

```TypeScript
function transformRotationMatrix(inRotationVector: Array<double>, coordinates: CoordinatesOptions): Promise<Array<double>>
```

根据指定坐标系映射旋转矩阵，使用Promise异步方式返回结果。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-sensor-function transformRotationMatrix(inRotationVector: Array<double>, coordinates: CoordinatesOptions): Promise<Array<double>>--><!--Device-sensor-function transformRotationMatrix(inRotationVector: Array<double>, coordinates: CoordinatesOptions): Promise<Array<double>>-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| inRotationVector | Array&lt;double&gt; | 是 | 旋转矩阵。 |
| coordinates | [CoordinatesOptions](arkts-sensorservice-sensor-coordinatesoptions-i.md) | 是 | 指定坐标系方向。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;double&gt;&gt; | Promise对象，使用异步方式返回转换后的旋转矩阵。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception; &lt;br&gt; 2. Sensor service ipc exception;3. Sensor data channel exception. |

