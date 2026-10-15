# getAngleModify

## 导入模块

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

<a id="getanglemodify1"></a>

## getAngleModify

```TypeScript
function getAngleModify(currentRotationMatrix: Array<number>, preRotationMatrix: Array<number>,
    callback: AsyncCallback<Array<number>>): void
```

获取两个旋转矩阵之间的角度变化。使用callback异步回调。

> **说明：** 
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用
> [sensor.getAngleVariation](arkts-sensorservice-sensor-getanglevariation-f.md)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getAngleVariation](arkts-sensorservice-sensor-getanglevariation-f.md)(currentRotationMatrix: Array&lt;number&gt;, preRotationMatrix: Array&lt;number&gt;, callback: AsyncCallback&lt;Array&lt;number&gt;&gt;)

<!--Device-sensor-function getAngleModify(currentRotationMatrix: Array<number>, preRotationMatrix: Array<number>,    callback: AsyncCallback<Array<number>>): void--><!--Device-sensor-function getAngleModify(currentRotationMatrix: Array<number>, preRotationMatrix: Array<number>,    callback: AsyncCallback<Array<number>>): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| currentRotationMatrix | Array&lt;number&gt; | 是 | 表示当前旋转矩阵。 |
| preRotationMatrix | Array&lt;number&gt; | 是 | 表示旋转矩阵。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;number&gt;&gt; | 是 | 异步返回z、x、y轴方向的旋转角度变化，单位：°（度）。 |

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


<a id="getanglemodify2"></a>

## getAngleModify

```TypeScript
function getAngleModify(currentRotationMatrix: Array<number>, preRotationMatrix: Array<number>): Promise<Array<number>>
```

获取两个旋转矩阵之间的角度变化。使用Promise异步回调。

> **说明：** 
> 
> 从API version 8 开始支持，从API version 9 开始废弃，建议使用
> [sensor.getAngleVariation](arkts-sensorservice-sensor-getanglevariation-f.md)替代。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** [getAngleVariation](arkts-sensorservice-sensor-getanglevariation-f.md)(currentRotationMatrix: Array&lt;number&gt;, preRotationMatrix: Array&lt;number&gt;)

<!--Device-sensor-function getAngleModify(currentRotationMatrix: Array<number>, preRotationMatrix: Array<number>): Promise<Array<number>>--><!--Device-sensor-function getAngleModify(currentRotationMatrix: Array<number>, preRotationMatrix: Array<number>): Promise<Array<number>>-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| currentRotationMatrix | Array&lt;number&gt; | 是 | 表示当前旋转矩阵。 |
| preRotationMatrix | Array&lt;number&gt; | 是 | 表示旋转矩阵。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;number&gt;&gt; | 使用异步方式返回z、x、y轴方向的旋转角度变化，单位：°（度）。 |

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
