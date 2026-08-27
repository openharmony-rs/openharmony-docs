# getSensorList

## 导入模块

```TypeScript
```

## getSensorList

```TypeScript
function getSensorList(callback: AsyncCallback<Array<Sensor>>): void
```

获取设备上的所有传感器信息。使用callback异步回调。如果需要同步获取传感器列表，请使用getSensorListSync。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;Sensor&gt;&gt; | 是 | 回调函数，异步返回传感器属性列表。 |

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
  sensor.getSensorList((err: BusinessError, data: Array<sensor.Sensor>) => {
    if (err) {
      console.error(`Failed to get sensorList. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    for (let i = 0; i < data.length; i++) {
      console.info('Succeeded in getting data[' + i + ']: ' + JSON.stringify(data[i]));
    }
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get sensorList. Code: ${e.code}, message: ${e.message}`);
}
```


## getSensorList

```TypeScript
function getSensorList(): Promise<Array<Sensor>>
```

获取设备上的所有传感器信息。使用Promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.Sensors.Sensor

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;Array & lt;Sensor & gt; & gt; | Promise对象，使用异步方式返回传感器属性列表。每个Sensor对象包含传感器的类型ID、名称、版本、厂商、最大范围、分辨率、功率等属性信息。 |

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
  sensor.getSensorList().then((data: Array<sensor.Sensor>) => {
    for (let i = 0; i < data.length; i++) {
      console.info('Succeeded in getting data[' + i + ']: ' + JSON.stringify(data[i]));
    }
  }, (err: BusinessError) => {
    console.error(`Failed to get sensorList. Code: ${err.code}, message: ${err.message}`);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get sensorList. Code: ${e.code}, message: ${e.message}`);
}
```
