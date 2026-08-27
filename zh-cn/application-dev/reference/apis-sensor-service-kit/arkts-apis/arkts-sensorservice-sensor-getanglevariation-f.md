# getAngleVariation

## 导入模块

```TypeScript
```

## getAngleVariation

```TypeScript
function getAngleVariation(currentRotationMatrix: Array<number>, preRotationMatrix: Array<number>,
    callback: AsyncCallback<Array<number>>): void
```

计算两个旋转矩阵之间的角度变化。使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| currentRotationMatrix | Array & lt;number & gt; | 是 | 当前旋转矩阵。 |
| preRotationMatrix | Array & lt;number & gt; | 是 | 相对旋转矩阵。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;number&gt;&gt; | 是 | 回调函数，异步返回绕z、x、y轴方向的旋转角度，单位：°（度）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;   2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception;   2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  // 旋转矩阵可以为3*3，或者4*4
  let currentRotationMatrix = [
    1, 0, 0,
    0, 1, 0,
    0, 0, 1
  ];
  let preRotationMatrix = [
    1, 0, 0,
    0, 0.87, -0.50,
    0, 0.50, 0.87
  ];
  sensor.getAngleVariation(currentRotationMatrix, preRotationMatrix, (err: BusinessError, data: Array<number>) => {
    if (err) {
      console.error(`Failed to get angle variation. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    if (data.length < 3) {
      console.error("Failed to get angle variation, length" + data.length);
      return;
    }
    console.info("Z: " + data[0]);
    console.info("X: " + data[1]);
    console.info("Y: " + data[2]);
  })
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get angle variation. Code: ${e.code}, message: ${e.message}`);
}
```


## getAngleVariation

```TypeScript
function getAngleVariation(currentRotationMatrix: Array<number>, preRotationMatrix: Array<number>): Promise<Array<number>>
```

得到两个旋转矩阵之间的角度变化。使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| currentRotationMatrix | Array & lt;number & gt; | 是 | 当前旋转矩阵。 |
| preRotationMatrix | Array & lt;number & gt; | 是 | 相对旋转矩阵。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;Array & lt;number & gt; & gt; | Promise对象，使用异步方式返回绕z、x、y轴方向的旋转角度，单位：°（度）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;   2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception;   2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// 使用try catch对可能出现的异常进行捕获
try {
  // 旋转矩阵可以为3*3，或者4*4
  let currentRotationMatrix = [
    1, 0, 0,
    0, 1, 0,
    0, 0, 1
  ];
  let preRotationMatrix = [
    1, 0, 0,
    0, 0.87, -0.50,
    0, 0.50, 0.87
  ];
  const promise = sensor.getAngleVariation(currentRotationMatrix, preRotationMatrix);
  promise.then((data: Array<number>) => {
    if (data.length < 3) {
      console.error("Failed to get angle variation, length" + data.length);
      return;
    }
    console.info("Z: " + data[0]);
    console.info("X: " + data[1]);
    console.info("Y: " + data[2]);
  }, (err: BusinessError) => {
    console.error(`Failed to get angle variation. Code: ${err.code}, message: ${err.message}`);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get angle variation. Code: ${e.code}, message: ${e.message}`);
}
```
