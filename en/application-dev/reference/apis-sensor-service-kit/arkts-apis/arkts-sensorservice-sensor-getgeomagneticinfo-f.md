# getGeomagneticInfo

## Modules to Import

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## getGeomagneticInfo

```TypeScript
function getGeomagneticInfo(locationOptions: LocationOptions, timeMillis: number, callback: AsyncCallback<GeomagneticResponse>): void
```

Obtains the geomagnetic field of a geographic location at a certain time. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| locationOptions | [LocationOptions](arkts-sensorservice-sensor-locationoptions-i.md) | Yes | Geographic location, including the longitude, latitude, and altitude. |
| timeMillis | number | Yes | Time when the magnetic declination is obtained. The value is a Unix timestamp, in ms. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[GeomagneticResponse](arkts-sensorservice-sensor-geomagneticresponse-i.md)&gt; | Yes | Callback used to return the geomagnetic field. |

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
  sensor.getGeomagneticInfo({ latitude: 80, longitude: 0, altitude: 0 }, 1580486400000,
      (err: BusinessError, data: sensor.GeomagneticResponse) => {
    if (err) {
      console.error(`Failed to get geomagneticInfo. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info("Succeeded in getting geomagneticInfo x" + data.x);
    console.info("Succeeded in getting geomagneticInfo y" + data.y);
    console.info("Succeeded in getting geomagneticInfo z" + data.z);
    console.info("Succeeded in getting geomagneticInfo geomagneticDip" + data.geomagneticDip);
    console.info("Succeeded in getting geomagneticInfo deflectionAngle" + data.deflectionAngle);
    console.info("Succeeded in getting geomagneticInfo levelIntensity" + data.levelIntensity);
    console.info("Succeeded in getting geomagneticInfo totalIntensity" + data.totalIntensity);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get geomagneticInfo. Code: ${e.code}, message: ${e.message}`);
}
```


<a id="getgeomagneticinfo-1"></a>

## getGeomagneticInfo

```TypeScript
function getGeomagneticInfo(locationOptions: LocationOptions, timeMillis: number): Promise<GeomagneticResponse>
```

Obtains the geomagnetic field of a geographic location at a certain time. This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| locationOptions | [LocationOptions](arkts-sensorservice-sensor-locationoptions-i.md) | Yes | Geographic location, including the longitude, latitude, and altitude. |
| timeMillis | number | Yes | Time when the magnetic declination is obtained. The value is a Unix timestamp, in ms. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[GeomagneticResponse](arkts-sensorservice-sensor-geomagneticresponse-i.md)&gt; | Promise used to return the geomagnetic field. |

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
  const promise = sensor.getGeomagneticInfo({ latitude: 80, longitude: 0, altitude: 0 }, 1580486400000);
  promise.then((data: sensor.GeomagneticResponse) => {
    console.info("Succeeded in getting geomagneticInfo x" + data.x);
    console.info("Succeeded in getting geomagneticInfo y" + data.y);
    console.info("Succeeded in getting geomagneticInfo z" + data.z);
    console.info("Succeeded in getting geomagneticInfo geomagneticDip" + data.geomagneticDip);
    console.info("Succeeded in getting geomagneticInfo deflectionAngle" + data.deflectionAngle);
    console.info("Succeeded in getting geomagneticInfo levelIntensity" + data.levelIntensity);
    console.info("Succeeded in getting geomagneticInfo totalIntensity" + data.totalIntensity);
  }, (err: BusinessError) => {
    console.error(`Failed to get geomagneticInfo. Code: ${err.code}, message: ${err.message}`);
  });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get geomagneticInfo. Code: ${e.code}, message: ${e.message}`);
}
```
