# createRotationMatrix

## Modules to Import

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## createRotationMatrix

```TypeScript
function createRotationMatrix(rotationVector: Array<number>, callback: AsyncCallback<Array<number>>): void
```

Converts a rotation vector into a rotation matrix. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getRotationMatrix](arkts-sensorservice-sensor-getrotationmatrix-f.md)(rotationVector: Array&lt;number&gt;, callback: AsyncCallback&lt;Array&lt;number&gt;&gt;)

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rotationVector | Array&lt;number&gt; | Yes | Rotation vector to convert. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;number&gt;&gt; | Yes | Callback used to return the rotation matrix. |

**Examples**

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


<a id="createrotationmatrix-1"></a>

## createRotationMatrix

```TypeScript
function createRotationMatrix(rotationVector: Array<number>): Promise<Array<number>>
```

Converts a rotation vector into a rotation matrix. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getRotationMatrix](arkts-sensorservice-sensor-getrotationmatrix-f.md)(rotationVector: Array&lt;number&gt;)

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rotationVector | Array&lt;number&gt; | Yes | Rotation vector to convert. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;number&gt;&gt; | Promise used to return the rotation matrix. |

**Examples**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

const promise = sensor.createRotationMatrix([0.20046076, 0.21907, 0.73978853, 0.60376877]);
promise.then((data: Array<number>) => {
  console.info('Succeeded in getting createRotationMatrix_promise');
  for (let i = 0; i < data.length; i++) {
    console.info('data[' + i + ']: ' + data[i]);
  }
}).catch((reason: BusinessError) => {
  console.info('Succeeded in getting promise::catch', reason);
})
```


<a id="createrotationmatrix-2"></a>

## createRotationMatrix

```TypeScript
function createRotationMatrix(gravity: Array<number>, geomagnetic: Array<number>, callback: AsyncCallback<RotationMatrixResponse>): void
```

Obtains the rotation matrix based on a gravity vector and geomagnetic vector. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getRotationMatrix](arkts-sensorservice-sensor-getrotationmatrix-f.md)(gravity: Array&lt;number&gt;, geomagnetic: Array&lt;number&gt;, callback: AsyncCallback&lt;RotationMatrixResponse&gt;)

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| gravity | Array&lt;number&gt; | Yes | Gravity vector. |
| geomagnetic | Array&lt;number&gt; | Yes | Geomagnetic vector. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[RotationMatrixResponse](arkts-sensorservice-sensor-rotationmatrixresponse-i.md)&gt; | Yes | Callback used to return the rotation matrix. |

**Examples**

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


<a id="createrotationmatrix-3"></a>

## createRotationMatrix

```TypeScript
function createRotationMatrix(gravity: Array<number>, geomagnetic: Array<number>,): Promise<RotationMatrixResponse>
```

Obtains the rotation matrix based on a gravity vector and geomagnetic vector. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getRotationMatrix](arkts-sensorservice-sensor-getrotationmatrix-f.md)(gravity: Array&lt;number&gt;, geomagnetic: Array&lt;number&gt;)

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| gravity | Array&lt;number&gt; | Yes | Gravity vector. |
| geomagnetic | Array&lt;number&gt; | Yes | Geomagnetic vector. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[RotationMatrixResponse](arkts-sensorservice-sensor-rotationmatrixresponse-i.md)&gt; | Promise used to return the rotation matrix. |

**Examples**

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

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

const promise = sensor.createRotationMatrix([0.20046076, 0.21907, 0.73978853, 0.60376877]);
promise.then((data: Array<number>) => {
  console.info('Succeeded in getting createRotationMatrix_promise');
  for (let i = 0; i < data.length; i++) {
    console.info('data[' + i + ']: ' + data[i]);
  }
}).catch((reason: BusinessError) => {
  console.info('Succeeded in getting promise::catch', reason);
})
```

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

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

const promise = sensor.createRotationMatrix([-0.27775216, 0.5351276, 9.788099], [210.87253, -78.6096, -111.44444]);
promise.then((data: sensor.RotationMatrixResponse) => {
  console.info(JSON.stringify(data));
}).catch((err: BusinessError) => {
  console.error(`Failed to get promise.`);
})
```
