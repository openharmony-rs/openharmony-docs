# getGeomagneticInfo

## 导入模块

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## getGeomagneticInfo

```TypeScript
function getGeomagneticInfo(locationOptions: LocationOptions, timeMillis: long, callback: AsyncCallback<GeomagneticResponse>): void
```

获取某时刻地球上特定位置的地磁场信息。使用callback异步回调。

**起始版本：** 23

<!--Device-sensor-function getGeomagneticInfo(locationOptions: LocationOptions, timeMillis: long, callback: AsyncCallback<GeomagneticResponse>): void--><!--Device-sensor-function getGeomagneticInfo(locationOptions: LocationOptions, timeMillis: long, callback: AsyncCallback<GeomagneticResponse>): void-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| locationOptions | [LocationOptions](arkts-sensorservice-sensor-locationoptions-i.md) | 是 | 地理位置，包括经度、纬度和海拔高度。 |
| timeMillis | long | 是 | 获取磁偏角的时间，unix时间戳，表示自1970-01-01 00:00:00 UTC以来的毫秒数。单位：ms（毫秒）。取值范围：正整数。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[GeomagneticResponse](arkts-sensorservice-sensor-geomagneticresponse-i.md)&gt; | 是 | 回调函数，异步返回地磁场信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception; <br> 2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.getGeomagneticInfo({ latitude: 80, longitude: 0, altitude: 0 }, 1580486400000,
    (err, data) => {
    let error = err as BusinessError;
    let dataValue = data as sensor.GeomagneticResponse;
      if (error) {
        console.error(`Failed to get geomagneticInfo. Code: ${error.code}, message: ${error.message}`);
        return;
      }
      console.info("Succeeded in getting geomagneticInfo x" + dataValue.x);
      console.info("Succeeded in getting geomagneticInfo y" + dataValue.y);
      console.info("Succeeded in getting geomagneticInfo z" + dataValue.z);
      console.info("Succeeded in getting geomagneticInfo geomagneticDip" + dataValue.geomagneticDip);
      console.info("Succeeded in getting geomagneticInfo deflectionAngle" + dataValue.deflectionAngle);
      console.info("Succeeded in getting geomagneticInfo levelIntensity" + dataValue.levelIntensity);
      console.info("Succeeded in getting geomagneticInfo totalIntensity" + dataValue.totalIntensity);
    });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get geomagneticInfo. Code: ${e.code}, message: ${e.message}`);
}
```

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
try {
  sensor.getGeomagneticInfo({ latitude: 80, longitude: 0, altitude: 0 }, 1580486400000,
    (err, data) => {
    let error = err as BusinessError;
    let dataValue = data as sensor.GeomagneticResponse;
      if (error) {
        console.error(`Failed to get geomagneticInfo. Code: ${error.code}, message: ${error.message}`);
        return;
      }
      console.info("Succeeded in getting geomagneticInfo x" + dataValue.x);
      console.info("Succeeded in getting geomagneticInfo y" + dataValue.y);
      console.info("Succeeded in getting geomagneticInfo z" + dataValue.z);
      console.info("Succeeded in getting geomagneticInfo geomagneticDip" + dataValue.geomagneticDip);
      console.info("Succeeded in getting geomagneticInfo deflectionAngle" + dataValue.deflectionAngle);
      console.info("Succeeded in getting geomagneticInfo levelIntensity" + dataValue.levelIntensity);
      console.info("Succeeded in getting geomagneticInfo totalIntensity" + dataValue.totalIntensity);
    });
} catch (error) {
  let e: BusinessError = error as BusinessError;
  console.error(`Failed to get geomagneticInfo. Code: ${e.code}, message: ${e.message}`);
}
```


## getGeomagneticInfo

```TypeScript
function getGeomagneticInfo(locationOptions: LocationOptions, timeMillis: long): Promise<GeomagneticResponse>
```

获取某时刻地球上特定位置的地磁场信息。使用Promise异步回调。

**起始版本：** 23

<!--Device-sensor-function getGeomagneticInfo(locationOptions: LocationOptions, timeMillis: long): Promise<GeomagneticResponse>--><!--Device-sensor-function getGeomagneticInfo(locationOptions: LocationOptions, timeMillis: long): Promise<GeomagneticResponse>-End-->

**系统能力：** SystemCapability.Sensors.Sensor

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| locationOptions | [LocationOptions](arkts-sensorservice-sensor-locationoptions-i.md) | 是 | 地理位置，包括经度、纬度和海拔高度。 |
| timeMillis | long | 是 | 获取磁偏角的时间，unix时间戳，表示自1970-01-01 00:00:00 UTC以来的毫秒数。单位：ms（毫秒）。取值范围：正整数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[GeomagneticResponse](arkts-sensorservice-sensor-geomagneticresponse-i.md)&gt; | Promise对象，使用异步方式返回地磁场信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br> 2. Incorrect parameter types; 3. Parameter verification failed. |
| [14500101](../errorcode-sensor.md#14500101-传感器服务异常) | Service exception. Possible causes: 1. Sensor hdf service exception; <br> 2. Sensor service ipc exception;3. Sensor data channel exception. |

**示例**

ArkTS-Dyn示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
import { sensor } from '@kit.SensorServiceKit';

// 使用try catch对可能出现的异常进行捕获
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

ArkTS-Sta示例：

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
   import { sensor } from '@kit.SensorServiceKit';
   
   // 使用try catch对可能出现的异常进行捕获
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

