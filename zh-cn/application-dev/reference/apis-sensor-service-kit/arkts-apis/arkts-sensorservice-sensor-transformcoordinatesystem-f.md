# transformCoordinateSystem

## transformCoordinateSystem

```TypeScript
function transformCoordinateSystem(inRotationVector: Array<number>, coordinates: CoordinatesOptions,
    callback: AsyncCallback<Array<number>>): void
```

旋转提供的旋转矩阵，使其可以以不同的方式表示坐标系，使用Callback异步方式返回结果。 > **说明：** > > 从API version 8 开始支持，从API version 9 开始废弃，建议使用 > [sensor.transformRotationMatrix] > [transformRotationMatrix](arkts-sensorservice-sensor-transformrotationmatrix-f.md#transformRotationMatrix) > 替代。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [transformRotationMatrix](arkts-sensorservice-sensor-transformrotationmatrix-f.md#transformRotationMatrix)(inRotationVector: Array&lt;double&gt;, coordinates: CoordinatesOptions, callback: AsyncCallback&lt;Array&lt;double&gt;&gt;)

<!--Device-sensor-function transformCoordinateSystem(inRotationVector: Array<number>, coordinates: CoordinatesOptions,    callback: AsyncCallback<Array<number>>): void--><!--Device-sensor-function transformCoordinateSystem(inRotationVector: Array<number>, coordinates: CoordinatesOptions,    callback: AsyncCallback<Array<number>>): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| inRotationVector | Array&lt;number&gt; | 是 | 表示旋转矩阵。 |
| coordinates | [CoordinatesOptions](arkts-sensorservice-sensor-coordinatesoptions-i.md) | 是 | 表示坐标系方向。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Array&lt;number&gt;&gt; | 是 | 异步返回转换后的旋转矩阵。 |

## 示例

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

sensor.transformCoordinateSystem([1, 0, 0, 0, 1, 0, 0, 0, 1], { x: 2, y: 3 }, 
                                 (err: BusinessError, data: Array<number>) => {
  if (err) {
    console.error(`Failed to operate. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info("Succeeded in starting Operation. Data obtained: " + data);
  for (let i = 0; i < data.length; i++) {
    console.info("Succeeded in getting transformCoordinateSystem data[ " + i + "] = " + data[i]);
  }
})
```


## transformCoordinateSystem

```TypeScript
function transformCoordinateSystem(inRotationVector: Array<number>, coordinates: CoordinatesOptions): Promise<Array<number>>
```

旋转提供的旋转矩阵，使其可以以不同的方式表示坐标系，使用Promise异步方式返回结果。 > **说明：** > > 从API version 8 开始支持，从API version 9 开始废弃，建议使用 > [sensor.transformRotationMatrix](arkts-sensorservice-sensor-transformrotationmatrix-f.md#transformRotationMatrix) > 替代。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [transformRotationMatrix](arkts-sensorservice-sensor-transformrotationmatrix-f.md#transformRotationMatrix)(inRotationVector: Array&lt;double&gt;, coordinates: CoordinatesOptions)

<!--Device-sensor-function transformCoordinateSystem(inRotationVector: Array<number>, coordinates: CoordinatesOptions): Promise<Array<number>>--><!--Device-sensor-function transformCoordinateSystem(inRotationVector: Array<number>, coordinates: CoordinatesOptions): Promise<Array<number>>-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| inRotationVector | Array&lt;number&gt; | 是 | 表示旋转矩阵。 |
| coordinates | [CoordinatesOptions](arkts-sensorservice-sensor-coordinatesoptions-i.md) | 是 | 表示坐标系方向。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;number&gt;&gt; | 使用异步方式返回转换后的旋转矩阵。 |

## 示例

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

const promise = sensor.transformCoordinateSystem([1, 0, 0, 0, 1, 0, 0, 0, 1], { x: 2, y: 3 });
promise.then((data: Array<number>) => {
  console.info("Succeeded in starting Operation");
  for (let i = 0; i < data.length; i++) {
    console.info("Succeeded in getting transformCoordinateSystem data[ " + i + "] = " + data[i]);
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to operate.`);
})
```

