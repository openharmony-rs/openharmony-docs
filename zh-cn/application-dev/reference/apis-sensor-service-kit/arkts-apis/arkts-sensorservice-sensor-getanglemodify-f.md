# getAngleModify

## getAngleModify

```TypeScript
function getAngleModify(currentRotationMatrix: Array<number>, preRotationMatrix: Array<number>,
    callback: AsyncCallback<Array<number>>): void
```

Obtains the angle change between two rotation matrices. This API uses an asynchronous callback to return the result.

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [sensor.getAngleVariation](arkts-sensorservice-sensor-getanglevariation-f.md#getanglevariation)(currentRotationMatrix:

<!--Device-sensor-function getAngleModify(currentRotationMatrix: Array<number>, preRotationMatrix: Array<number>,    callback: AsyncCallback<Array<number>>): void--><!--Device-sensor-function getAngleModify(currentRotationMatrix: Array<number>, preRotationMatrix: Array<number>,    callback: AsyncCallback<Array<number>>): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| currentRotationMatrix | Array&lt;number&gt; | 是 | Current rotation matrix. |
| preRotationMatrix | Array&lt;number&gt; | 是 | The other rotation matrix. |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;Array&lt;number&gt;&gt; | 是 | Callback used to return the angle change around the z, x, and y axes, in degrees. |

**示例：**

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

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [sensor.getAngleVariation](arkts-sensorservice-sensor-getanglevariation-f.md#getanglevariation)(currentRotationMatrix:

<!--Device-sensor-function getAngleModify(currentRotationMatrix: Array<number>, preRotationMatrix: Array<number>): Promise<Array<number>>--><!--Device-sensor-function getAngleModify(currentRotationMatrix: Array<number>, preRotationMatrix: Array<number>): Promise<Array<number>>-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| currentRotationMatrix | Array&lt;number&gt; | 是 | Current rotation matrix. |
| preRotationMatrix | Array&lt;number&gt; | 是 | The other rotation matrix. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;number&gt;&gt; | Promise used to return the angle change around the z, x, and y axes, in |

**示例：**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

const promise = sensor.getAngleModify([1, 0, 0, 0, 1, 0, 0, 0, 1], [1, 0, 0, 0, 0.87, -0.50, 0, 0.50, 0.87]);
promise.then((data: Array<number>) => {
  console.info('Succeeded in getting AngleModify_promise.');
  for (let i = 0; i < data.length; i++) {
    console.info("Succeeded in getting data[" + i + "]: " + data[i]);
  }
}).catch((reason: BusinessError) => {
  let e: BusinessError = reason as BusinessError;
  console.info("Succeeded in getting promise::catch", e);
})
```

