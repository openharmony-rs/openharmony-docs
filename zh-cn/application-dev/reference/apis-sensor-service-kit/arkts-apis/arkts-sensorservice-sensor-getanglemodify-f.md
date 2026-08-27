# getAngleModify

## 导入模块

```TypeScript
```

## getAngleModify

```TypeScript
function getAngleModify(currentRotationMatrix: Array<number>, preRotationMatrix: Array<number>,
    callback: AsyncCallback<Array<number>>): void
```

Obtains the angle change between two rotation matrices. This API uses an asynchronous callback to return the result.

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getAngleVariation](arkts-sensorservice-sensor-getanglevariation-f.md)(currentRotationMatrix: Array&lt;double&gt;, preRotationMatrix: Array&lt;double&gt;, callback: AsyncCallback&lt;Array&lt;double&gt;&gt;)

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| currentRotationMatrix | Array & lt;number & gt; | 是 | Current rotation matrix. |
| preRotationMatrix | Array & lt;number & gt; | 是 | The other rotation matrix. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;number&gt;&gt; | 是 | Callback used to return the angle change around the z, x, and y axes, in degrees. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

sensor.getAngleModify([1, 0, 0, 0, 1, 0, 0, 0, 1], [1, 0, 0, 0, 0.87, -0.50, 0, 0.50, 0.87],
                      (err: BusinessError, data: Array<number>) => {
  if (err) {
    console.error(`Failed to register data. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  for (let i = 0; i < data.length; i++) {
    console.info("data[" + i + "]: " + data[i]);
  }
})
```


## getAngleModify

```TypeScript
function getAngleModify(currentRotationMatrix: Array<number>, preRotationMatrix: Array<number>): Promise<Array<number>>
```

Obtains the angle change between two rotation matrices. This API uses a promise to return the result.

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getAngleVariation](arkts-sensorservice-sensor-getanglevariation-f.md)(currentRotationMatrix: Array&lt;double&gt;, preRotationMatrix: Array&lt;double&gt;)

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| currentRotationMatrix | Array & lt;number & gt; | 是 | Current rotation matrix. |
| preRotationMatrix | Array & lt;number & gt; | 是 | The other rotation matrix. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;Array & lt;number & gt; & gt; | Promise used to return the angle change around the z, x, and y axes, in degrees. |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

const promise = sensor.getAngleModify([1, 0, 0, 0, 1, 0, 0, 0, 1], [1, 0, 0, 0, 0.87, -0.50, 0, 0.50, 0.87]);
promise.then((data: Array<number>) => {
  console.info('Succeeded in getting AngleModify_promise.');
  for (let i = 0; i < data.length; i++) {
    console.info('Succeeded in getting data[' + i + ']: ' + data[i]);
  }
}).catch((reason: BusinessError) => {
  let e: BusinessError = reason as BusinessError;
  console.info('Succeeded in getting promise::catch', e);
})
```
