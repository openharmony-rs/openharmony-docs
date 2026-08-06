# createQuaternion

## createQuaternion

```TypeScript
function createQuaternion(rotationVector: Array<number>, callback: AsyncCallback<Array<number>>): void
```

将旋转矢量转换为四元数，使用Callback异步方式返回结果。 > **说明**： > > 从API version 8 开始支持，从API version 9 开始废弃，建议使用 > [sensor.getQuaternion]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ > 替代。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [sensor.getQuaternion](arkts-sensorservice-sensor-getquaternion-f.md#getquaternion)(rotationVector:

<!--Device-sensor-function createQuaternion(rotationVector: Array<number>, callback: AsyncCallback<Array<number>>): void--><!--Device-sensor-function createQuaternion(rotationVector: Array<number>, callback: AsyncCallback<Array<number>>): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rotationVector | Array&lt;number&gt; | 是 | 表示旋转矢量。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;Array&lt;number&gt;&gt; | 是 | 异步返回四元数。 |

**示例：**

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

将旋转矢量转换为四元数，使用Promise异步方式返回结果。 > **说明**： > > 从API version 8 开始支持，从API version 9 开始废弃，建议使用 > [sensor.getQuaternion]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_替代。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [sensor.getQuaternion](arkts-sensorservice-sensor-getquaternion-f.md#getquaternion)(rotationVector:

<!--Device-sensor-function createQuaternion(rotationVector: Array<number>): Promise<Array<number>>--><!--Device-sensor-function createQuaternion(rotationVector: Array<number>): Promise<Array<number>>-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rotationVector | Array&lt;number&gt; | 是 | 表示旋转矢量。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;number&gt;&gt; | 使用异步方式返回四元数。 |

**示例：**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

const promise = sensor.createQuaternion([0.20046076, 0.21907, 0.73978853, 0.60376877]);
promise.then((data: Array<number>) => {
  console.info('Succeeded in getting createQuaternion_promise');
  for (let i = 0; i < data.length; i++) {
    console.info("data[" + i + "]: " + data[i]);
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to get promise.`);
})
```

