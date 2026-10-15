# getDirection

## Modules to Import

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

<a id="getdirection1"></a>

## getDirection

```TypeScript
function getDirection(rotationMatrix: Array<number>, callback: AsyncCallback<Array<number>>): void
```

Obtains the device direction based on the rotation matrix. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use
> [sensor.getOrientation](arkts-sensorservice-sensor-getorientation-f.md)
> instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getOrientation](arkts-sensorservice-sensor-getorientation-f.md)(rotationMatrix: Array&lt;number&gt;, callback: AsyncCallback&lt;Array&lt;number&gt;&gt;)

<!--Device-sensor-function getDirection(rotationMatrix: Array<number>, callback: AsyncCallback<Array<number>>): void--><!--Device-sensor-function getDirection(rotationMatrix: Array<number>, callback: AsyncCallback<Array<number>>): void-End-->

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rotationMatrix | Array&lt;number&gt; | Yes | The other rotation matrix. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;number&gt;&gt; | Yes | Asynchronous callback used to return the rotation angles around the z, x, and y axes, in degrees (°). |

**Examples**

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


<a id="getdirection2"></a>

## getDirection

```TypeScript
function getDirection(rotationMatrix: Array<number>): Promise<Array<number>>
```

Obtains the device direction based on the rotation matrix. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API is supported since API version 8 and deprecated since API version 9. You are advised to use
> [sensor.getOrientation](arkts-sensorservice-sensor-getorientation-f.md) instead.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getOrientation](arkts-sensorservice-sensor-getorientation-f.md)(rotationMatrix: Array&lt;number&gt;)

<!--Device-sensor-function getDirection(rotationMatrix: Array<number>): Promise<Array<number>>--><!--Device-sensor-function getDirection(rotationMatrix: Array<number>): Promise<Array<number>>-End-->

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rotationMatrix | Array&lt;number&gt; | Yes | The other rotation matrix. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;number&gt;&gt; | Promise used to return the rotation angles around the z, x, and y axes, in degrees (°). |

**Examples**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

const promise = sensor.getDirection([1, 0, 0, 0, 1, 0, 0, 0, 1]);
promise.then((data: Array<number>) => {
  console.info('Succeeded in getting sensor_getDirection_Promise', data);
  for (let i = 1; i < data.length; i++) {
    console.info('Succeeded in getting sensor_getDirection_promise' + data[i]);
  }
}).catch((err: BusinessError) => {
  console.error(`Failed to get promise.`);
})
```
