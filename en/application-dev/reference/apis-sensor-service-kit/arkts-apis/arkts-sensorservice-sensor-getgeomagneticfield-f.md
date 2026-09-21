# getGeomagneticField

## Modules to Import

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## getGeomagneticField

```TypeScript
function getGeomagneticField(locationOptions: LocationOptions, timeMillis: number, callback: AsyncCallback<GeomagneticResponse>): void
```

Obtains the geomagnetic field of a geographic location. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getGeomagneticInfo](arkts-sensorservice-sensor-getgeomagneticinfo-f.md)(locationOptions: LocationOptions, timeMillis: number, callback: AsyncCallback&lt;GeomagneticResponse&gt;)

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| locationOptions | [LocationOptions](arkts-sensorservice-sensor-locationoptions-i.md) | Yes | Geographic location. |
| timeMillis | number | Yes | Time for obtaining the magnetic declination, in milliseconds. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[GeomagneticResponse](arkts-sensorservice-sensor-geomagneticresponse-i.md)&gt; | Yes | Callback used to return the geomagnetic field. |

**Examples**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

sensor.getGeomagneticField({ latitude: 80, longitude: 0, altitude: 0 }, 1580486400000, 
                           (err: BusinessError, data: sensor.GeomagneticResponse) => {
  if (err) {
    console.error(`Failed to operate. Code: ${err.code}, message: ${err.message}`);
    return;
  }
  console.info('Succeeded in getting sensor_getGeomagneticField_callback x: ' + data.x + ',y: ' + data.y + ',z: ' +
  data.z + ',geomagneticDip: ' + data.geomagneticDip + ',deflectionAngle: ' + data.deflectionAngle +
  ',levelIntensity: ' + data.levelIntensity + ',totalIntensity: ' + data.totalIntensity);
});
```


<a id="getgeomagneticfield-1"></a>

## getGeomagneticField

```TypeScript
function getGeomagneticField(locationOptions: LocationOptions, timeMillis: number): Promise<GeomagneticResponse>
```

Obtains the geomagnetic field of a geographic location. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getGeomagneticInfo](arkts-sensorservice-sensor-getgeomagneticinfo-f.md)(locationOptions: LocationOptions, timeMillis: number)

**System capability:** SystemCapability.Sensors.Sensor

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| locationOptions | [LocationOptions](arkts-sensorservice-sensor-locationoptions-i.md) | Yes | Geographic location. |
| timeMillis | number | Yes | Time for obtaining the magnetic declination, in milliseconds. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[GeomagneticResponse](arkts-sensorservice-sensor-geomagneticresponse-i.md)&gt; | Promise used to return the geomagnetic field. |

**Examples**

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

const promise = sensor.getGeomagneticField({ latitude: 80, longitude: 0, altitude: 0 }, 1580486400000);
promise.then((data: sensor.GeomagneticResponse) => {
  console.info('Succeeded in getting sensor_getGeomagneticField_promise x: ' + data.x + ',y: ' + data.y + ',z: ' +
  data.z + ',geomagneticDip: ' + data.geomagneticDip + ',deflectionAngle: ' + data.deflectionAngle +
  ',levelIntensity: ' + data.levelIntensity + ',totalIntensity: ' + data.totalIntensity);
}).catch((reason: BusinessError) => {
  console.error(`Failed to operate.`);
})
```
