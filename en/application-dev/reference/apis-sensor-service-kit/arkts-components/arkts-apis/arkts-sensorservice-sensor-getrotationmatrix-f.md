# getRotationMatrix

## Modules to Import

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## getRotationMatrix

```TypeScript
function getRotationMatrix(rotationVector: Array<number>, callback: AsyncCallback<Array<number>>): void
```

Obtains the rotation matrix from a rotation vector. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rotationVector | Array&lt;number&gt; | Yes | Rotation vector. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;number&gt;&gt; | Yes | Callback used to return the rotation matrix. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-service-exception) | Service exception. Possible causes: 1. Sensor hdf service exception;<br> 2. Sensor service ipc exception;3. Sensor data channel exception. |

**Examples**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
try {
  let rotationVector = [0.20046076, 0.21907, 0.73978853, 0.60376877];
  sensor.getRotationMatrix(rotationVector, (err: BusinessError, data: Array<number>) => {
    if (err) {
      console.error(`Failed to get rotationMatrix. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    for (let i = 0; i < data.length; i++) {
      console.info('Succeeded in getting data[' + i + ']: ' + data[i]);
    }
  })
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get rotationMatrix. Code: ${e.code}, message: ${e.message}`);
}
```


<a id="getrotationmatrix-1"></a>

## getRotationMatrix

```TypeScript
function getRotationMatrix(rotationVector: Array<number>): Promise<Array<number>>
```

Obtains the rotation matrix from a rotation vector. This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rotationVector | Array&lt;number&gt; | Yes | Rotation vector. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;number&gt;&gt; | Promise used to return the rotation matrix. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-service-exception) | Service exception. Possible causes: 1. Sensor hdf service exception;<br> 2. Sensor service ipc exception;3. Sensor data channel exception. |

**Examples**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
try {
  let rotationVector = [0.20046076, 0.21907, 0.73978853, 0.60376877];
  const promise = sensor.getRotationMatrix(rotationVector);
  promise.then((data: Array<number>) => {
    for (let i = 0; i < data.length; i++) {
      console.info('Succeeded in getting data[' + i + ']: ' + data[i]);
    }
  }, (err: BusinessError) => {
    console.error(`Failed to get rotationMatrix. Code: ${err.code}, message: ${err.message}`);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get rotationMatrix. Code: ${e.code}, message: ${e.message}`);
}
```


<a id="getrotationmatrix-2"></a>

## getRotationMatrix

```TypeScript
function getRotationMatrix(gravity: Array<number>, geomagnetic: Array<number>, callback: AsyncCallback<RotationMatrixResponse>): void
```

Obtains the rotation matrix based on a gravity vector and geomagnetic vector. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| gravity | Array&lt;number&gt; | Yes | Gravity vector. |
| geomagnetic | Array&lt;number&gt; | Yes | Geomagnetic vector. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[RotationMatrixResponse](arkts-sensorservice-sensor-rotationmatrixresponse-i.md)&gt; | Yes | Callback used to return the rotation matrix. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-service-exception) | Service exception. Possible causes: 1. Sensor hdf service exception;<br> 2. Sensor service ipc exception;3. Sensor data channel exception. |

**Examples**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
try {
  let gravity = [-0.27775216, 0.5351276, 9.788099];
  let geomagnetic = [210.87253, -78.6096, -111.44444];
  sensor.getRotationMatrix(gravity, geomagnetic, (err: BusinessError, data: sensor.RotationMatrixResponse) => {
    if (err) {
      console.error(`Failed to get rotationMatrix. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in getting rotationMatrix' + JSON.stringify(data));
  })
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get rotationMatrix. Code: ${e.code}, message: ${e.message}`);
}
```


<a id="getrotationmatrix-3"></a>

## getRotationMatrix

```TypeScript
function getRotationMatrix(gravity: Array<number>, geomagnetic: Array<number>): Promise<RotationMatrixResponse>
```

Obtains the rotation matrix based on a gravity vector and geomagnetic vector. This API uses a promise to return the result.

**Since:** 9

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

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-service-exception) | Service exception. Possible causes: 1. Sensor hdf service exception;<br> 2. Sensor service ipc exception;3. Sensor data channel exception. |

**Examples**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Use try catch to capture possible exceptions.
try {
  let gravity = [-0.27775216, 0.5351276, 9.788099];
  let geomagnetic = [210.87253, -78.6096, -111.44444];
  const promise = sensor.getRotationMatrix(gravity, geomagnetic);
  promise.then((data: sensor.RotationMatrixResponse) => {
    console.info('Succeeded in getting rotationMatrix' + JSON.stringify(data));
  }, (err: BusinessError) => {
    console.error(`Failed to get rotationMatrix. Code: ${err.code}, message: ${err.message}`);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get rotationMatrix. Code: ${e.code}, message: ${e.message}`);
}
```
