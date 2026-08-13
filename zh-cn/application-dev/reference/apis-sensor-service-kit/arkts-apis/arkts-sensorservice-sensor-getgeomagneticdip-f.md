# getGeomagneticDip

## getGeomagneticDip

```TypeScript
function getGeomagneticDip(inclinationMatrix: Array<number>, callback: AsyncCallback<number>): void
```

根据倾斜矩阵计算地磁倾斜角，使用Callback异步方式返回结果。 > **说明：** > > 从API version 8 开始支持，从API version 9 开始废弃，建议使用 > [sensor.getInclination](arkts-sensorservice-sensor-getinclination-f.md#getInclination) > 替代。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [getInclination](arkts-sensorservice-sensor-getinclination-f.md#getInclination)(inclinationMatrix: Array&lt;double&gt;, callback: AsyncCallback&lt;double&gt;)

<!--Device-sensor-function getGeomagneticDip(inclinationMatrix: Array<number>, callback: AsyncCallback<number>): void--><!--Device-sensor-function getGeomagneticDip(inclinationMatrix: Array<number>, callback: AsyncCallback<number>): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| inclinationMatrix | Array&lt;number&gt; | 是 | 表示倾斜矩阵。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;number&gt; | 是 | 异步返回地磁倾斜角，单位为弧度。 |

## 示例

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

sensor.getGeomagneticDip([1, 0, 0, 0, 1, 0, 0, 0, 1], (err: BusinessError, data: number) => {
  if (err) {
    console.error(`Failed to register data. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info("Succeeded in getting getGeomagneticDip interface get data: " + data);
})
```


## getGeomagneticDip

```TypeScript
function getGeomagneticDip(inclinationMatrix: Array<number>): Promise<number>
```

根据倾斜矩阵计算地磁倾斜角，使用Promise异步方式返回结果。 > **说明：** > > 从API version 8 开始支持，从API version 9 开始废弃，建议使用 > [sensor.getInclination](arkts-sensorservice-sensor-getinclination-f.md#getInclination)替代。

**起始版本：** 8

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为8。

**废弃版本：** 9

**替代接口：** [getInclination](arkts-sensorservice-sensor-getinclination-f.md#getInclination)(inclinationMatrix: Array&lt;double&gt;)

<!--Device-sensor-function getGeomagneticDip(inclinationMatrix: Array<number>): Promise<number>--><!--Device-sensor-function getGeomagneticDip(inclinationMatrix: Array<number>): Promise<number>-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| inclinationMatrix | Array&lt;number&gt; | 是 | 表示倾斜矩阵。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | 使用异步方式返回地磁倾斜角，单位为弧度。 |

## 示例

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

const promise = sensor.getGeomagneticDip([1, 0, 0, 0, 1, 0, 0, 0, 1]);
promise.then((data: number) => {
  console.info('Succeeded in get GeomagneticDip_promise', data);
}).catch((err: BusinessError) => {
  console.error(`Failed to operate.`);
})
```

