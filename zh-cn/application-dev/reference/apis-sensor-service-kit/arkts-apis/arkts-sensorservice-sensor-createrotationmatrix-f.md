# createRotationMatrix

## createRotationMatrix

```TypeScript
function createRotationMatrix(rotationVector: Array<number>, callback: AsyncCallback<Array<number>>): void
```

将旋转矢量转换为旋转矩阵，使用Callback异步方式返回结果。 > **说明**： > > 从API version 8 开始支持，从API version 9 开始废弃，建议使用 > [sensor.getRotationMatrix]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ > 替代。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [sensor.getRotationMatrix](arkts-sensorservice-sensor-getrotationmatrix-f.md#getrotationmatrix)(rotationVector:

<!--Device-sensor-function createRotationMatrix(rotationVector: Array<number>, callback: AsyncCallback<Array<number>>): void--><!--Device-sensor-function createRotationMatrix(rotationVector: Array<number>, callback: AsyncCallback<Array<number>>): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rotationVector | Array&lt;number&gt; | 是 | 表示旋转矢量。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;Array&lt;number&gt;&gt; | 是 | 异步返回旋转矩阵。 |

**示例：**

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

将旋转矢量转换为旋转矩阵，使用Promise异步方式返回结果。 > **说明**： > > 从API version 8 开始支持，从API version 9 开始废弃，建议使用 > [sensor.getRotationMatrix]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_替代。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [sensor.getRotationMatrix](arkts-sensorservice-sensor-getrotationmatrix-f.md#getrotationmatrix)(rotationVector:

<!--Device-sensor-function createRotationMatrix(rotationVector: Array<number>): Promise<Array<number>>--><!--Device-sensor-function createRotationMatrix(rotationVector: Array<number>): Promise<Array<number>>-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rotationVector | Array&lt;number&gt; | 是 | 表示旋转矢量。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;number&gt;&gt; | 使用异步方式返回旋转矩阵。 |

**示例：**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

const promise = sensor.createRotationMatrix([0.20046076, 0.21907, 0.73978853, 0.60376877]);
promise.then((data: Array<number>) => {
  console.info('Succeeded in getting createRotationMatrix_promise');
  for (let i = 0; i < data.length; i++) {
    console.info("data[" + i + "]: " + data[i]);
  }
}).catch((reason: BusinessError) => {
  console.info("Succeeded in getting promise::catch", reason);
})
```


## createRotationMatrix

```TypeScript
function createRotationMatrix(gravity: Array<number>, geomagnetic: Array<number>, callback: AsyncCallback<RotationMatrixResponse>): void
```

根据重力矢量和地磁矢量计算旋转矩阵，使用Callback异步方式返回结果。 > **说明**： > > 从API version 8 开始支持，从API version 9 开始废弃，建议使用 > [sensor.getRotationMatrix]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ > 替代。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [sensor.getRotationMatrix](arkts-sensorservice-sensor-getrotationmatrix-f.md#getrotationmatrix)(gravity:

<!--Device-sensor-function createRotationMatrix(gravity: Array<number>, geomagnetic: Array<number>, callback: AsyncCallback<RotationMatrixResponse>): void--><!--Device-sensor-function createRotationMatrix(gravity: Array<number>, geomagnetic: Array<number>, callback: AsyncCallback<RotationMatrixResponse>): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| gravity | Array&lt;number&gt; | 是 | 表示重力向量。 |
| geomagnetic | Array&lt;number&gt; | 是 | 表示地磁矢量。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;RotationMatrixResponse&gt; | 是 | 异步返回旋转矩阵。 |

**示例：**

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

根据重力矢量和地磁矢量计算旋转矩阵，使用Promise异步方式返回结果。 > **说明**： > > 从API version 8 开始支持，从API version 9 开始废弃，建议使用 > [sensor.getRotationMatrix]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_替代。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [sensor.getRotationMatrix](arkts-sensorservice-sensor-getrotationmatrix-f.md#getrotationmatrix)(gravity:

<!--Device-sensor-function createRotationMatrix(gravity: Array<number>, geomagnetic: Array<number>,): Promise<RotationMatrixResponse>--><!--Device-sensor-function createRotationMatrix(gravity: Array<number>, geomagnetic: Array<number>,): Promise<RotationMatrixResponse>-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| gravity | Array&lt;number&gt; | 是 | 表示重力向量。 |
| geomagnetic | Array&lt;number&gt; | 是 | 表示地磁矢量。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;RotationMatrixResponse&gt; | 使用异步方式返回旋转矩阵。 |

