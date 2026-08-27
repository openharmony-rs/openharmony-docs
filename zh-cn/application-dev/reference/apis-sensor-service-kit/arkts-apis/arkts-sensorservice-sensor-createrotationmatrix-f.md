# createRotationMatrix

## 导入模块

```TypeScript
```

## createRotationMatrix

```TypeScript
function createRotationMatrix(rotationVector: Array<number>, callback: AsyncCallback<Array<number>>): void
```

将旋转矢量转换为旋转矩阵。使用callback异步回调。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用
> [sensor.getRotationMatrix](arkts-sensorservice-sensor-getrotationmatrix-f.md)
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getRotationMatrix](arkts-sensorservice-sensor-getrotationmatrix-f.md)(rotationVector: Array&lt;double&gt;, callback: AsyncCallback&lt;Array&lt;double&gt;&gt;)

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rotationVector | Array & lt;number & gt; | 是 | 表示旋转矢量。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;number&gt;&gt; | 是 | 异步返回旋转矩阵。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

sensor.createRotationMatrix([0.20046076, 0.21907, 0.73978853, 0.60376877],
                            (err: BusinessError, data: Array<number>) => {
  if (err) {
    console.error(`Failed to register data. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  for (let i = 0; i < data.length; i++) {
    console.info("Succeeded in getting data[" + i + "]: " + data[i]);
  }
})
```


## createRotationMatrix

```TypeScript
function createRotationMatrix(rotationVector: Array<number>): Promise<Array<number>>
```

将旋转矢量转换为旋转矩阵。使用Promise异步回调。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用
> [sensor.getRotationMatrix](arkts-sensorservice-sensor-getrotationmatrix-f.md)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getRotationMatrix](arkts-sensorservice-sensor-getrotationmatrix-f.md)(rotationVector: Array&lt;double&gt;)

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rotationVector | Array & lt;number & gt; | 是 | 表示旋转矢量。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;Array & lt;number & gt; & gt; | 使用异步方式返回旋转矩阵。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

const promise = sensor.createRotationMatrix([0.20046076, 0.21907, 0.73978853, 0.60376877]);
promise.then((data: Array<number>) => {
  console.info('Succeeded in getting createRotationMatrix_promise');
  for (let i = 0; i < data.length; i++) {
    console.info('data[' + i + ']: ' + data[i]);
  }
}).catch((reason: BusinessError) => {
  console.info('Succeeded in getting promise::catch', reason);
})
```


## createRotationMatrix

```TypeScript
function createRotationMatrix(gravity: Array<number>, geomagnetic: Array<number>, callback: AsyncCallback<RotationMatrixResponse>): void
```

根据重力矢量和地磁矢量计算旋转矩阵。使用callback异步回调。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用
> [sensor.getRotationMatrix](arkts-sensorservice-sensor-getrotationmatrix-f.md)
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getRotationMatrix](arkts-sensorservice-sensor-getrotationmatrix-f.md)(gravity: Array&lt;double&gt;, geomagnetic: Array&lt;double&gt;, callback: AsyncCallback&lt;RotationMatrixResponse&gt;)

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| gravity | Array & lt;number & gt; | 是 | 表示重力向量。 |
| geomagnetic | Array & lt;number & gt; | 是 | 表示地磁矢量。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[RotationMatrixResponse](arkts-sensorservice-sensor-rotationmatrixresponse-i.md)&gt; | 是 | 异步返回旋转矩阵。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

sensor.createRotationMatrix([-0.27775216, 0.5351276, 9.788099], [210.87253, -78.6096, -111.44444], 
                            (err: BusinessError, data: sensor.RotationMatrixResponse) => {
  if (err) {
    console.error(`Failed to get create rotationMatrix. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(JSON.stringify(data));
})
```


## createRotationMatrix

```TypeScript
function createRotationMatrix(gravity: Array<number>, geomagnetic: Array<number>,): Promise<RotationMatrixResponse>
```

根据重力矢量和地磁矢量计算旋转矩阵。使用Promise异步回调。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用
> [sensor.getRotationMatrix](arkts-sensorservice-sensor-getrotationmatrix-f.md)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getRotationMatrix](arkts-sensorservice-sensor-getrotationmatrix-f.md)(gravity: Array&lt;double&gt;, geomagnetic: Array&lt;double&gt;)

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| gravity | Array & lt;number & gt; | 是 | 表示重力向量。 |
| geomagnetic | Array & lt;number & gt; | 是 | 表示地磁矢量。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[RotationMatrixResponse](arkts-sensorservice-sensor-rotationmatrixresponse-i.md)&gt; | 使用异步方式返回旋转矩阵。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

sensor.createRotationMatrix([0.20046076, 0.21907, 0.73978853, 0.60376877],
                            (err: BusinessError, data: Array<number>) => {
  if (err) {
    console.error(`Failed to register data. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  for (let i = 0; i < data.length; i++) {
    console.info("Succeeded in getting data[" + i + "]: " + data[i]);
  }
})
```

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

const promise = sensor.createRotationMatrix([0.20046076, 0.21907, 0.73978853, 0.60376877]);
promise.then((data: Array<number>) => {
  console.info('Succeeded in getting createRotationMatrix_promise');
  for (let i = 0; i < data.length; i++) {
    console.info('data[' + i + ']: ' + data[i]);
  }
}).catch((reason: BusinessError) => {
  console.info('Succeeded in getting promise::catch', reason);
})
```

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

sensor.createRotationMatrix([-0.27775216, 0.5351276, 9.788099], [210.87253, -78.6096, -111.44444], 
                            (err: BusinessError, data: sensor.RotationMatrixResponse) => {
  if (err) {
    console.error(`Failed to get create rotationMatrix. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info(JSON.stringify(data));
})
```

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

const promise = sensor.createRotationMatrix([-0.27775216, 0.5351276, 9.788099], [210.87253, -78.6096, -111.44444]);
promise.then((data: sensor.RotationMatrixResponse) => {
  console.info(JSON.stringify(data));
}).catch((err: BusinessError) => {
  console.error(`Failed to get promise.`);
})
```
