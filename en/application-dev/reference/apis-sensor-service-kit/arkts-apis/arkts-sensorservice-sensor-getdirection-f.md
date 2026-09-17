# getDirection

## Modules to Import

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## getDirection

```TypeScript
function getDirection(rotationMatrix: Array<number>, callback: AsyncCallback<Array<number>>): void
```

Obtains the device direction based on the rotation matrix. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getOrientation](arkts-sensorservice-sensor-getorientation-f.md)(rotationMatrix: Array&lt;number&gt;, callback: AsyncCallback&lt;Array&lt;number&gt;&gt;)

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rotationMatrix | Array&lt;number&gt; | Yes | Rotation matrix. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;number&gt;&gt; | Yes | Callback used to return the rotation angle around the z, x, and y axes, in degrees. |

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


## getDirection

```TypeScript
function getDirection(rotationMatrix: Array<number>): Promise<Array<number>>
```

Obtains the device direction based on the rotation matrix. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getOrientation](arkts-sensorservice-sensor-getorientation-f.md)(rotationMatrix: Array&lt;number&gt;)

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rotationMatrix | Array&lt;number&gt; | Yes | Rotation matrix. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;number&gt;&gt; | Promise used to return the rotation angle around the z, x, and y axes, in degrees. |

**Examples**

See [getDirection](#getdirection)
