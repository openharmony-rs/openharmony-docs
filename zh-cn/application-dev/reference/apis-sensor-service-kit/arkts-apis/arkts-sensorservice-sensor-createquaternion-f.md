# createQuaternion

## 导入模块

```TypeScript
```

## createQuaternion

```TypeScript
function createQuaternion(rotationVector: Array<number>, callback: AsyncCallback<Array<number>>): void
```

将旋转矢量转换为四元数。使用callback异步回调。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用
> [sensor.getQuaternion](arkts-sensorservice-sensor-getquaternion-f.md)
> 替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getQuaternion](arkts-sensorservice-sensor-getquaternion-f.md)(rotationVector: Array&lt;double&gt;, callback: AsyncCallback&lt;Array&lt;double&gt;&gt;)

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rotationVector | Array & lt;number & gt; | 是 | 表示旋转矢量。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;number&gt;&gt; | 是 | 异步返回四元数。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

sensor.createQuaternion([0.20046076, 0.21907, 0.73978853, 0.60376877],
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


## createQuaternion

```TypeScript
function createQuaternion(rotationVector: Array<number>): Promise<Array<number>>
```

将旋转矢量转换为四元数。使用Promise异步回调。

> **说明：**
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用
> [sensor.getQuaternion](arkts-sensorservice-sensor-getquaternion-f.md)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getQuaternion](arkts-sensorservice-sensor-getquaternion-f.md)(rotationVector: Array&lt;double&gt;)

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rotationVector | Array & lt;number & gt; | 是 | 表示旋转矢量。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;Array & lt;number & gt; & gt; | 使用异步方式返回四元数。 |

**示例**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

const promise = sensor.createQuaternion([0.20046076, 0.21907, 0.73978853, 0.60376877]);
promise.then((data: Array<number>) => {
  console.info('Succeeded in getting createQuaternion_promise');
  for (let i = 0; i < data.length; i++) {
    console.info('data[' + i + ']: ' + data[i]);
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to get promise.`);
})
```
