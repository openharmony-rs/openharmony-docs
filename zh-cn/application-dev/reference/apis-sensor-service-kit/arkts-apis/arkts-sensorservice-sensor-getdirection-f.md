# getDirection

## getDirection

```TypeScript
function getDirection(rotationMatrix: Array<number>, callback: AsyncCallback<Array<number>>): void
```

根据旋转矩阵计算设备的方向，使用Callback异步方式返回结果。 > **说明**： > > 从API version 8 开始支持，从API version 9 开始废弃，建议使用 > [sensor.getOrientation]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_ > 替代。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [sensor.getOrientation](arkts-sensorservice-sensor-getorientation-f.md#getorientation)(rotationMatrix:

<!--Device-sensor-function getDirection(rotationMatrix: Array<number>, callback: AsyncCallback<Array<number>>): void--><!--Device-sensor-function getDirection(rotationMatrix: Array<number>, callback: AsyncCallback<Array<number>>): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rotationMatrix | Array&lt;number&gt; | 是 | 表示旋转矩阵。 |
| callback | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;Array&lt;number&gt;&gt; | 是 | 异步返回围绕z、x、y轴方向的旋转角度，单位度（°）。 |

**示例：**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

sensor.getDirection([1, 0, 0, 0, 1, 0, 0, 0, 1], (err: BusinessError, data: Array<number>) => {
  if (err) {
    console.error(`Failed to register data. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info("Succeeded in getting getDirection interface get data: " + data);
  for (let i = 1; i < data.length; i++) {
    console.info("Succeeded in getting sensor_getDirection_callback" + data[i]);
  }
})
```


## getDirection

```TypeScript
function getDirection(rotationMatrix: Array<number>): Promise<Array<number>>
```

根据旋转矩阵计算设备的方向，使用Promise异步方式返回结果。 > **说明**： > > 从API version 8 开始支持，从API version 9 开始废弃，建议使用 > [sensor.getOrientation]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_替代。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [sensor.getOrientation](arkts-sensorservice-sensor-getorientation-f.md#getorientation)(rotationMatrix:

<!--Device-sensor-function getDirection(rotationMatrix: Array<number>): Promise<Array<number>>--><!--Device-sensor-function getDirection(rotationMatrix: Array<number>): Promise<Array<number>>-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rotationMatrix | Array&lt;number&gt; | 是 | 表示旋转矩阵。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;number&gt;&gt; | 使用异步方式返回围绕z、x、y轴方向的旋转角度，单位度（°）。 |

**示例：**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

const promise = sensor.getDirection([1, 0, 0, 0, 1, 0, 0, 0, 1]);
promise.then((data: Array<number>) => {
  console.info('Succeeded in getting sensor_getDirection_Promise', data);
  for (let i = 1; i < data.length; i++) {
    console.info("Succeeded in getting sensor_getDirection_promise" + data[i]);
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to get promise.`);
})
```

