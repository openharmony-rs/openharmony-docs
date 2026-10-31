# @system.sensor (Sensor)
<!--Kit: Sensor Service Kit-->
<!--Subsystem: Sensors-->
<!--Owner: @dilligencer-->
<!--Designer: @LiuChao-->
<!--Tester: @zhaofangyuan-->
<!--Adviser: @hu-zhiqiong-->

The **@system.sensor** module is a sensor data subscription module for lite wearables. It provides the data subscription and subscription cancellation capabilities for the acceleration, compass, distance, ambient light, pedometer, barometric pressure, heart rate, device wearing status, device orientation, and gyroscope sensors.

This module helps apps obtain sensor data change notifications in real time to implement functions such as fitness monitoring, health tracking, environment sensing, direction identification, and screen adaptation. Each sensor provides subscription and unsubscription APIs. The wearing status sensor additionally provides the **getOnBodyState** API for a single query.

For devices other than lightweight wearables, this module is no longer maintained since API version 8. You are advised to use the [@ohos.sensor](js-apis-sensor.md) module instead.

This module uses the subscription-unsubscription mode. You can call **subscribe** to subscribe to data, and the data will be reported through a callback when it changes. You can call **unsubscribe** to cancel the subscription. **subscribe** and **unsubscribe** must be used in pairs. If an app subscribes to the same sensor multiple times, only the last subscription takes effect. For the acceleration, device orientation, and gyroscope sensors, you can configure the callback frequency using **interval**. The default value is **normal** (200 ms per callback).

All APIs require hardware support and can be debugged only on real devices. Some APIs may have device behavior differences. For details, see the description of each API.

> **NOTE**
>
> - Module maintenance policy:
>     - For lite wearables, this module is constantly maintained and available.
>     - For other device types, this module is no longer maintained since API version 8, and you are advised to use the new [@ohos.sensor](js-apis-sensor.md) module.
> - The initial APIs of this module are supported since API version 3. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - This module requires hardware support and can only be debugged on real devices.
> - To reduce performance overhead, you are advised to unsubscribe from the sensor data in the **onDestroy** callback.

## Modules to Import

```ts
import { Sensor } from '@kit.SensorServiceKit';
```

## Sensor

### Sensor.subscribeAccelerometer

 static subscribeAccelerometer(options: subscribeAccelerometerOptions): void

Subscribes to data changes of the acceleration sensor. Obtains the acceleration data of the device along the x, y, and z axes through a callback. The data is in the format of an **AccelerometerResponse** object, which contains three number fields of **x**, **y**, and **z**.

This API can be used to obtain the acceleration information of a device to implement functions such as motion detection and shake.

After this API is called, the system reports acceleration data at the specified callback frequency. If this API is called multiple times for the same app, the last call takes effect.

> **NOTE**
>
> For devices other than lite wearables, you are advised to use [ACCELEROMETER](js-apis-sensor.md#sensoronsensortypesensor_type_id_accelerometerdeprecated) since API version 8.

**System capability**: SystemCapability.Sensors.Sensor.Lite

**Required permissions**: ohos.permission.ACCELEROMETER

**Parameters**

| Name | Type                                                        | Mandatory| Description                                      |
| ------- | ------------------------------------------------------------ | ---- | ------------------------------------------ |
| options | [subscribeAccelerometerOptions](#subscribeaccelerometeroptions) | Yes  | Parameters for subscribing to the acceleration sensor, including the callback frequency and callback function.|

**ArkTS example**

```ts
import { Sensor, AccelerometerResponse, subscribeAccelerometerOptions } from '@kit.SensorServiceKit';

let accelerometerOptions: subscribeAccelerometerOptions = {
  interval: 'normal',
  success: (ret: AccelerometerResponse) => {
    console.info('Succeeded in subscribing. X-axis data: ' + ret.x);
    console.info('Succeeded in subscribing. Y-axis data: ' + ret.y);
    console.info('Succeeded in subscribing. Z-axis data: ' + ret.z);
  },
  fail: (data: string, code: number) => {
    console.error(`Failed to subscribe. Code: ${code}, data: ${data}`);
  },
};
Sensor.subscribeAccelerometer(accelerometerOptions);
```

**JS example**

```js
import Sensor from '@system.sensor';

let subscribeAccelerometerOptions = {
  interval: 'normal',
  success: (ret) => {
    console.info('Succeeded in subscribing. X-axis data: ' + ret.x);
    console.info('Succeeded in subscribing. Y-axis data: ' + ret.y);
    console.info('Succeeded in subscribing. Z-axis data: ' + ret.z);
  },
  fail: (data, code) => {
    console.error(`Failed to subscribe. Code: ${code}, data: ${data}`);
  },
};
Sensor.subscribeAccelerometer(subscribeAccelerometerOptions);
```

```xml
<!-- xxx.hml -->
<div class="container">
  <text class="title">
    {{ title }}
  </text>
  <text class="TextArea">{{ TextContent }}</text>
  <picker-view type="text" range="{{ sensorList }}" selected="
    {{ defaultSelect }}" @change="pickerOnchange" class="pickerText">
  </picker-view>
  <div class="BUTTON">
    <input class="buttonText" type="button" onclick="subscribe">Subscribe</input>
    <text class="EmptyText"></text>
    <input class="buttonText" type="button" onclick="unsubscribe">Unsubscribe</input>
  </div>
</div>
```

```css
/* xxx.css */
.container {
  flex-direction: column;
  justify-content: flex-start;
  align-items: flex-start;
  width: 100%;
  height: 100%;
  background-color: #F1F3F5;
}
.title {
  font-size: 20px;
  text-align: center;
  width: 100%;
  height: 50px;
  margin-top: 10px;
  color: black;
}
.pickerText {
  width: 100%;
  height: 60px;
  margin-bottom: 30px;
  margin-top: 30px;
  selected-color: black;
}
.EmptyText {
  width: 30px;
  margin-left: 20px;
}
.TextArea {
  background-color: white;
  border-radius: 0px;
  color: black;
  height: 100px;
  width: 100%;
  font-size: 17px;
  font-weight: bold;
  margin-bottom: 10px;
  margin-top: 10px;
  align-content: center;
  align-items: center;
  text-align: center;
}
.buttonText {
  background-color: blue;
  radius: 30px;
  text-color: white;
  font-size: 25px;
  width: 100px;
  height: 100%;
  margin-top: 5px;
  margin-left: 80px;
  font-weight: bolder;
}
.BUTTON {
  width: 100%;
  height: 60px;
  margin-bottom: 5px;
  margin-top: 5px;
}
```

```js
// xxx.js
import sensor from '@system.sensor';

export default {
  data: {
    TAG: "WearLiteSample:",
    title: "LiteWearableDemo",
    TextContent: "AAA",
    sensorList: ['ACCELEROMETER', 'MAGNETIC_FIELD', 'PROXIMITY',
      'AMBIENT_LIGHT', 'PEDOMETER', 'BAROMETER',
      'HEART_RATE', 'WEAR_DETECTION', 'ORIENTATION', 'GYROSCOPE', 'getOnBodyState'],
    defaultSelect: '',
    currentSelect: 'ACCELEROMETER'
  },

  onInit() {
    this.defaultSelect = 'ACCELEROMETER';
  },


  pickerOnchange(e) {
    console.info(this.TAG + 'current selected:' + e.newValue);
    this.currentSelect = e.newValue;
  },

  subscribe() {
    try {
      switch (this.currentSelect) {
        case "ACCELEROMETER":
          let subscribeAccelerometerOptions = {
            interval: 'normal',
            success: (ret) => {
              console.info(this.TAG + 'Succeeded in subscribing. X-axis data: ' + ret.x);
              console.info(this.TAG + 'Succeeded in subscribing. Y-axis data: ' + ret.y);
              console.info(this.TAG + 'Succeeded in subscribing. Z-axis data: ' + ret.z);
              this.TextContent = JSON.stringify(ret);
            },
            fail: (data, code) => {
              console.error(this.TAG + `Failed to subscribe. Code: ${code}, data: ${data}`);
            },
          };
          sensor.subscribeAccelerometer(subscribeAccelerometerOptions);
          break;
        case "MAGNETIC_FIELD":
          let subscribeCompassOptions = {
            success: (ret) => {
              console.info(this.TAG + 'Succeeded in subscribing. Get data direction:' + ret.direction);
              this.TextContent = JSON.stringify(ret);
            },
            fail: (data, code) => {
              console.error(`Failed to subscribe. Code: ${code}, data: ${data}`);
            },
          };
          sensor.subscribeCompass(subscribeCompassOptions);
          break;
        case "PROXIMITY":
          let subscribeProximityOptions = {
            success: (ret) => {
              console.info(this.TAG + 'Succeeded in subscribing. Get data distance:' + ret.distance);
              this.TextContent = JSON.stringify(ret);
            },
            fail: (data, code) => {
              console.error(`Failed to subscribe. Code: ${code}, data: ${data}`);
            },
          };
          sensor.subscribeProximity(subscribeProximityOptions);
          break;
        case "AMBIENT_LIGHT":
          let subscribeLightOptions = {
            success: (ret) => {
              console.info(this.TAG + 'Succeeded in subscribing. Get data intensity:' + ret.intensity);
              this.TextContent = JSON.stringify(ret);
            },
            fail: (data, code) => {
              console.error(`Failed to subscribe. Code: ${code}, data: ${data}`);
            },
          };
          sensor.subscribeLight(subscribeLightOptions);
          break;
        case "PEDOMETER":
          let subscribeStepCounterOptions = {
            success: (ret) => {
              console.info(this.TAG + 'Succeeded in subscribing. Get step value:' + ret.steps);
              this.TextContent = JSON.stringify(ret);
            },
            fail: (data, code) => {
              console.error(`Failed to subscribe. Code: ${code}, data: ${data}`);
            },
          };
          sensor.subscribeStepCounter(subscribeStepCounterOptions);
          break;
        case "BAROMETER":
          let subscribeBarometerOptions = {
            success: (ret) => {
              console.info(this.TAG + 'Succeeded in subscribing. Get data value:' + ret.pressure);
              this.TextContent = JSON.stringify(ret);
            },
            fail: (data, code) => {
              console.error(`Failed to subscribe. Code: ${code}, data: ${data}`);
            },
            };
            sensor.subscribeBarometer(subscribeBarometerOptions);
            break;
        case "HEART_RATE":
          let subscribeHeartRateOptions = {
            success: (ret) => {
              console.info(this.TAG + 'Succeeded in subscribing. Get heartRate value:' + ret.heartRate);
              this.TextContent = JSON.stringify(ret);
            },
            fail: (data, code) => {
              console.error(`Failed to subscribe. Code: ${code}, data: ${data}`);
            },
          };
          sensor.subscribeHeartRate(subscribeHeartRateOptions);
          break;
        case "WEAR_DETECTION":
          let subscribeOnBodyStateOptions = {
            success: (ret) => {
              console.info(this.TAG + 'Succeeded in subscribing. Get on-body state value:' + ret.value);
              this.TextContent = JSON.stringify(ret);
            },
            fail: (data, code) => {
              console.error(`Failed to subscribe. Code: ${code}, data: ${data}`);
            },
          };
          sensor.subscribeOnBodyState(subscribeOnBodyStateOptions);
          break;
        case "ORIENTATION":
          let subscribeDeviceOrientationOptions = {
            interval: 'normal',
            success: (ret) => {
              console.info(this.TAG + 'Succeeded in subscribing. Alpha data: ' + ret.alpha);
              console.info(this.TAG + 'Succeeded in subscribing. Beta data: ' + ret.beta);
              console.info(this.TAG + 'Succeeded in subscribing. Gamma data: ' + ret.gamma);
              this.TextContent = JSON.stringify(ret);
            },
            fail: (data, code) => {
              console.error(`Failed to subscribe. Code: ${code}, data: ${data}`);
            }
          };
          sensor.subscribeDeviceOrientation(subscribeDeviceOrientationOptions);
          break;
        case "GYROSCOPE":
          let subscribeGyroscopeOptions = {
            interval: 'normal',
            success: (ret) => {
              console.info(this.TAG + 'Succeeded in subscribing. X-axis data: ' + ret.x);
              console.info(this.TAG + 'Succeeded in subscribing. Y-axis data: ' + ret.y);
              console.info(this.TAG + 'Succeeded in subscribing. Z-axis data: ' + ret.z);
              this.TextContent = JSON.stringify(ret);
            },
            fail: (data, code) => {
              console.error(`Failed to subscribe. Code: ${code}, data: ${data}`);
            }
          };
          sensor.subscribeGyroscope(subscribeGyroscopeOptions);
          break;
        case "getOnBodyState":
          let getOnBodyStateOptions = {
            success: (ret) => {
              console.info(this.TAG + 'Succeeded in getting. On body state: ' + ret.value);
              this.TextContent = JSON.stringify(ret);
            },
            fail: (data, code) => {
              console.error(`Failed to subscribe. Code: ${code}, data: ${data}`);
            },
          };
          sensor.getOnBodyState(getOnBodyStateOptions);
          break;
      }
    } catch (e) {
      console.error(this.TAG + `subscribe exception occurred, code: ${e.code}, message: ${e.message}`)
    }
  },

  unsubscribe() {
    try {
      switch (this.currentSelect) {
        case "ACCELEROMETER":
          sensor.unsubscribeAccelerometer();
          break;
        case "MAGNETIC_FIELD":
          sensor.unsubscribeCompass();
          break;
        case "PROXIMITY":
          sensor.unsubscribeProximity();
          break;
        case "AMBIENT_LIGHT":
          sensor.unsubscribeLight();
          break;
        case "PEDOMETER":
          sensor.unsubscribeStepCounter();
          break;
        case "BAROMETER":
          sensor.unsubscribeBarometer();
          break;
        case "HEART_RATE":
          sensor.unsubscribeHeartRate();
          break;
        case "WEAR_DETECTION":
          sensor.unsubscribeOnBodyState();
          break;
        case "ORIENTATION":
          sensor.unsubscribeDeviceOrientation();
          break;
        case "GYROSCOPE":
          sensor.unsubscribeGyroscope();
          break;
        }
        this.TextContent = "";
    } catch (e) {
        console.error(this.TAG + `unsubscribe exception occurred, code: ${e.code}, message: ${e.message}`);
    }
  }
}
```

### Sensor.unsubscribeAccelerometer

static unsubscribeAccelerometer(): void

Unsubscribes from data of the acceleration sensor. After this method is called, the callback for the acceleration sensor will not be triggered.

When the acceleration sensor data is no longer needed (for example, when the page is switched or the app is exited), call this method to cancel the subscription to reduce system resource usage.

After this method is called, the callback registered using **subscribeAccelerometer** will not be triggered. To obtain data again, call **subscribeAccelerometer** again.

> **NOTE**
>
> For devices other than lite wearables, you are advised to use [ACCELEROMETER](js-apis-sensor.md#sensoroffsensortypesensor_type_id_accelerometerdeprecated) instead since API version 8.

**System capability**: SystemCapability.Sensors.Sensor.Lite

**Required permissions**: ohos.permission.ACCELEROMETER

**ArkTS example**

```ts
Sensor.unsubscribeAccelerometer();
```

**JS example**

```js
Sensor.unsubscribeAccelerometer();
```

### Sensor.subscribeCompass

 static subscribeCompass(options: SubscribeCompassOptions): void

Subscribes to data changes of the compass sensor. Obtains the device direction data through a callback. The data is in the format of a **CompassResponse object**, which contains the **direction** field.

This API can be used to obtain the device direction information to implement functions such as navigation and compass.

After this API is called, the system reports the device direction data when the compass data changes. If this API is called multiple times for the same app, the last call takes effect.

> **NOTE**
>
> For devices other than lite wearables, you are advised to use [ORIENTATION](js-apis-sensor.md#sensoronsensortypesensor_type_id_orientationdeprecated) instead since API version 8.

**System capability**: SystemCapability.Sensors.Sensor.Lite

**Parameters**

| Name | Type                                               | Mandatory| Description                            |
| ------- | --------------------------------------------------- | ---- | -------------------------------- |
| options | [SubscribeCompassOptions](#subscribecompassoptions) | Yes  | Parameters for subscribing to the compass sensor, including the callback.|

**ArkTS example**

```ts
import { Sensor, CompassResponse, SubscribeCompassOptions } from '@kit.SensorServiceKit';

let subscribeCompassOptions: SubscribeCompassOptions = {
  success: (ret: CompassResponse) => {
    console.info('Succeeded in subscribing. Get data direction:' + ret.direction);
  },
  fail: (data: string, code: number) => {
    console.error(`Failed to subscribe. Code: ${code}, data: ${data}`);
  },
};
Sensor.subscribeCompass(subscribeCompassOptions);
```

**JS example**

```js
import Sensor from '@system.sensor';

let subscribeCompassOptions = {
  success: (ret) => {
    console.info('Succeeded in subscribing. Get data direction:' + ret.direction);
  },
  fail: (data, code) => {
    console.error(`Failed to subscribe. Code: ${code}, data: ${data}`);
  },
};
Sensor.subscribeCompass(subscribeCompassOptions);
```

### Sensor.unsubscribeCompass

static unsubscribeCompass(): void

Unsubscribes from data of the compass sensor. After this method is called, the callback for the compass sensor will not be triggered.

Call this method to cancel the subscription when the compass sensor data is no longer needed.

After this method is called, the callback registered using **subscribeCompass** will not be triggered. You need to call **subscribeCompass** to register to the callback before calling this method for unsubscription. Otherwise, this method will not take effect.

> **NOTE**
>
> For devices other than lite wearables, you are advised to use [ORIENTATION](js-apis-sensor.md#sensoroffsensortypesensor_type_id_orientationdeprecated) instead since API version 8.

**System capability**: SystemCapability.Sensors.Sensor.Lite

**ArkTS example**

```ts
Sensor.unsubscribeCompass();
```

**JS example**

```js
Sensor.unsubscribeCompass();
```

### Sensor.subscribeProximity

 static subscribeProximity(options: SubscribeProximityOptions): void

Subscribes to data changes of the proximity sensor. Obtains the distance between a visible object and the device screen through the callback function. The data is in the format of the **ProximityResponse** object, which contains the **distance** field.

This API can be used to detect the distance between an object and the device screen to implement functions such as automatic screen-off during calls and mistouch prevention.

After this API is called, the system reports data when the data of the proximity sensor changes. If this API is called multiple times for the same app, only the last call takes effect.

> **NOTE**
>
> This API is supported since API version 3 and deprecated since API version 8. For devices other than lite wearables, you are advised to use [PROXIMITY](js-apis-sensor.md#sensoronsensortypesensor_type_id_proximitydeprecated) instead.

**System capability**: SystemCapability.Sensors.Sensor.Lite

**Device behavior differences**: This API can be called on wearables and lite wearables, but has no effect on other device types.

**Parameters**

| Name | Type                                                   | Mandatory| Description                            |
| ------- | ------------------------------------------------------- | ---- | -------------------------------- |
| options | [SubscribeProximityOptions](#subscribeproximityoptions) | Yes  | Sets the parameters for subscribing to the distance sensor, including the callback function.|

**ArkTS example**

```ts
import { Sensor, ProximityResponse, SubscribeProximityOptions } from '@kit.SensorServiceKit';

let subscribeProximityOptions: SubscribeProximityOptions = {
  success: (ret: ProximityResponse) => {
    console.info('Succeeded in subscribing. Get data distance:' + ret.distance);
  },
  fail: (data: string, code: number) => {
    console.error(`Failed to subscribe. Code: ${code}, data: ${data}`);
  },
};
Sensor.subscribeProximity(subscribeProximityOptions);
```

**JS example**

```js
import Sensor from '@system.sensor';

let subscribeProximityOptions = {
  success: (ret) => {
    console.info('Succeeded in subscribing. Get data distance:' + ret.distance);
  },
  fail: (data, code) => {
    console.error(`Failed to subscribe. Code: ${code}, data: ${data}`);
  },
};
sensor.subscribeProximity(subscribeProximityOptions);
```

### Sensor.unsubscribeProximity

static unsubscribeProximity(): void

Unsubscribes from data of the distance sensor. After this method is called, the callback for the distance sensor will not be triggered.

When the distance sensor data is no longer needed, call this method to cancel the subscription.

After this method is called, the callback registered using **subscribeProximity** will not be triggered. You need to call **subscribeProximity** to register to the callback before calling this method for unsubscription. Otherwise, this method will not take effect.

> **NOTE**
>
> For devices other than lite wearables, you are advised to use [PROXIMITY](js-apis-sensor.md#sensoroffsensortypesensor_type_id_proximitydeprecated) instead since API version 8.

**System capability**: SystemCapability.Sensors.Sensor.Lite

**Device behavior differences**: This API can be called on wearables and lite wearables, but has no effect on other device types.

**ArkTS example**

```ts
Sensor.unsubscribeProximity();
```

**JS example**

```js
Sensor.unsubscribeProximity();
```

### Sensor.subscribeLight

 static subscribeLight(options: SubscribeLightOptions): void

Subscribes to ambient light sensor data changes. The ambient light intensity data is obtained through a callback function. The data is in the format of a **LightResponse** object, which contains the **intensity** field. The unit is lux.

This API is used when you need to obtain the ambient light intensity to implement functions such as automatic screen brightness adjustment and ambient light detection.

If this API is called multiple times, the last call takes effect.

> **NOTE**
>
> For devices other than lite wearables, you are advised to use [AMBIENT_LIGHT](js-apis-sensor.md#sensoronsensortypesensor_type_id_ambient_lightdeprecated) instead since API version 8.

**System capability**: SystemCapability.Sensors.Sensor.Lite

**Device behavior differences**: This API can be called on wearables and lite wearables, but has no effect on other device types.

**Parameters**

| Name | Type                                           | Mandatory| Description                              |
| ------- | ----------------------------------------------- | ---- | ---------------------------------- |
| options | [SubscribeLightOptions](#subscribelightoptions) | Yes  | Type of data to return.|

**ArkTS example**

```ts
import { Sensor, LightResponse, SubscribeLightOptions } from '@kit.SensorServiceKit';

let subscribeLightOptions: SubscribeLightOptions = {
  success: (ret: LightResponse) => {
    console.info('Succeeded in subscribing. Get data intensity:' + ret.intensity);
  },
  fail: (data: string, code: number) => {
    console.error(`Failed to subscribe. Code: ${code}, data: ${data}`);
  },
};
Sensor.subscribeLight(subscribeLightOptions);
```

**JS example**

```js
import Sensor from '@system.sensor';

let subscribeLightOptions = {
  success: (ret) => {
    console.info('Succeeded in subscribing. Get data intensity:' + ret.intensity);
  },
  fail: (data, code) => {
    console.error(`Failed to subscribe. Code: ${code}, data: ${data}`);
  },
};
sensor.subscribeLight(subscribeLightOptions);
```

### Sensor.unsubscribeLight

static unsubscribeLight(): void

Unsubscribes from data of the ambient light sensor. After this method is called, the callback for the ambient light sensor will not be triggered.

When the ambient light sensor data is no longer needed, call this method to cancel the subscription.

After this method is called, the callback registered using **subscribeLight** will not be triggered. You need to call **subscribeLight** to register to the callback before calling this method for unsubscription. Otherwise, this method will not take effect.

> **NOTE**
>
> For devices other than lite wearables, you are advised to use [AMBIENT_LIGHT](js-apis-sensor.md#sensoroffsensortypesensor_type_id_ambient_lightdeprecated) instead since API version 8.

**System capability**: SystemCapability.Sensors.Sensor.Lite

**Device behavior differences**: This API can be called on wearables and lite wearables, but has no effect on other device types.

**ArkTS example**

```ts
Sensor.unsubscribeLight();
```

**JS example**

```js
Sensor.unsubscribeLight();
```

### Sensor.subscribeStepCounter

 static subscribeStepCounter(options: SubscribeStepCounterOptions): void

Subscribes to data changes of the step counter sensor. Callback function used to obtain the number of steps counted after the step counter sensor is restarted. The data is in the format of a **StepCounterResponse** object, which contains the steps field.

This API can be used to obtain the user's step count to implement functions such as step counting, fitness tracking, and health monitoring.

After this API is called, the system reports data when the step count data changes. If this API is called multiple times for the same app, the last call takes effect.

> **NOTE**
>
>  For devices other than lite wearables, you are advised to use [PEDOMETER](js-apis-sensor.md#sensoronsensortypesensor_type_id_pedometerdeprecated) instead since API version 8.

**System capability**: SystemCapability.Sensors.Sensor.Lite

**Required permissions**: ohos.permission.ACTIVITY_MOTION

**Parameters**

| Name | Type                                                       | Mandatory| Description                                  |
| ------- | ----------------------------------------------------------- | ---- | -------------------------------------- |
| options | [SubscribeStepCounterOptions](#subscribestepcounteroptions) | Yes  | Type of data to return.|

**ArkTS example**

```ts
import { Sensor, StepCounterResponse, SubscribeStepCounterOptions } from '@kit.SensorServiceKit';

let subscribeStepCounterOptions: SubscribeStepCounterOptions = {
  success: (ret: StepCounterResponse) => {
    console.info('Succeeded in subscribing. Get step value:' + ret.steps);
  },
  fail: (data: string, code: number) => {
    console.error(`Failed to subscribe. Code: ${code}, data: ${data}`);
  },
};
Sensor.subscribeStepCounter(subscribeStepCounterOptions);
```

**JS example**

```js
import Sensor from '@system.sensor';

let subscribeStepCounterOptions = {
  success: (ret) => {
    console.info('Succeeded in subscribing. Get step value:' + ret.steps);
  },
  fail: (data, code) => {
    console.error(`Failed to subscribe. Code: ${code}, data: ${data}`);
  },
};
sensor.subscribeStepCounter(subscribeStepCounterOptions);
```

### Sensor.unsubscribeStepCounter

static unsubscribeStepCounter(): void

Unsubscribes from data of the pedometer sensor. After this method is called, the callback for the pedometer sensor will not be triggered.

Call this method to cancel the subscription when the step count data is no longer needed.

After this method is called, the callback registered using **subscribeStepCounter** will not be triggered. You need to call **subscribeStepCounter** to register to the callback before calling this method for unsubscription. Otherwise, the unsubscription will not take effect.

> **NOTE**
>
> For devices other than lite wearables, you are advised to use [PEDOMETER](js-apis-sensor.md#sensoroffsensortypesensor_type_id_pedometerdeprecated) instead since API version 8.

**System capability**: SystemCapability.Sensors.Sensor.Lite

**Required permissions**: ohos.permission.ACTIVITY_MOTION

**ArkTS example**

```ts
Sensor.unsubscribeStepCounter();
```

**JS example**

```js
Sensor.unsubscribeStepCounter();
```


### Sensor.subscribeBarometer

static subscribeBarometer(options: SubscribeBarometerOptions): void

Subscribes to data changes of the barometer sensor. The atmospheric pressure value is obtained through the callback function. The data is in the format of a **BarometerResponse** object, which contains the **pressure** field. The unit is Pa.

This API can be used to obtain the atmospheric pressure information to implement functions such as altitude estimation, weather monitoring, and indoor navigation.

After this API is called, the system reports data when the barometric pressure changes. If this API is called multiple times for the same app, the last call takes effect.

> **NOTE**
>
> For devices other than lite wearables, you are advised to use [BAROMETER](js-apis-sensor.md#sensoronsensortypesensor_type_id_barometerdeprecated) instead since API version 8.

**System capability**: SystemCapability.Sensors.Sensor.Lite

**Parameters**

| Name | Type                                                   | Mandatory| Description                              |
| ------- | ------------------------------------------------------- | ---- | ---------------------------------- |
| options | [SubscribeBarometerOptions](#subscribebarometeroptions) | Yes  | Type of data to return.|

**ArkTS example**

```ts
import { Sensor, BarometerResponse, SubscribeBarometerOptions } from '@kit.SensorServiceKit';

let subscribeBarometerOptions: SubscribeBarometerOptions = {
  success: (ret: BarometerResponse) => {
    console.info('Succeeded in subscribing. Get data value:' + ret.pressure);
  },
  fail: (data: string, code: number) => {
    console.error(`Failed to subscribe. Code: ${code}, data: ${data}`);
  },
};
Sensor.subscribeBarometer(subscribeBarometerOptions);
```

**JS example**

```js
import Sensor from '@system.sensor';

let subscribeBarometerOptions = {
  success: (ret) => {
    console.info('Succeeded in subscribing. Get data value:' + ret.pressure);
  },
  fail: (data, code) => {
    console.error(`Failed to subscribe. Code: ${code}, data: ${data}`);
  },
};
sensor.subscribeBarometer(subscribeBarometerOptions);
```


### Sensor.unsubscribeBarometer

static unsubscribeBarometer(): void

Unsubscribes from data of the barometer sensor. After this method is called, the callback for the barometer sensor will not be triggered.

Call this method to cancel the subscription when the barometric pressure data is no longer needed.

After this method is called, the callback function registered using **subscribeBarometer** will not be triggered. You need to call **subscribeBarometer** to register to the callback before calling this method for unsubscription. Otherwise, this method will not take effect.

> **NOTE**
>
> For devices other than lite wearables, you are advised to use [BAROMETER](js-apis-sensor.md#sensoroffsensortypesensor_type_id_barometerdeprecated) instead since API version 8.

**System capability**: SystemCapability.Sensors.Sensor.Lite

**ArkTS example**

```ts
Sensor.unsubscribeBarometer();
```

**JS example**

```js
Sensor.unsubscribeBarometer();
```


### Sensor.subscribeHeartRate

 static subscribeHeartRate(options: SubscribeHeartRateOptions): void

Subscribes to data changes of the heart rate sensor. Obtains the heart rate data through the callback function. The data is in the format of a **HeartRateResponse** object, which contains the **heartRate** field. The unit is bpm. The default callback frequency is once every 5 seconds.

This API can be used to obtain the user's heart rate data to implement functions such as health monitoring and exercise intensity evaluation.

After this API is called, the system reports heart rate data every 5 seconds. If this API is called multiple times for the same app, the last call takes effect.

> **NOTE**
>
> For devices other than lite wearables, you are advised to use [HEART_RATE](js-apis-sensor.md#sensoronsensortypesensor_type_id_heart_ratedeprecated) instead since API version 8.

**System capability**: SystemCapability.Sensors.Sensor.Lite

**Required permissions**: ohos.permission.READ_HEALTH_DATA

**Parameters**

| Name | Type                                                   | Mandatory| Description                            |
| ------- | ------------------------------------------------------- | ---- | -------------------------------- |
| options | [SubscribeHeartRateOptions](#subscribeheartrateoptions) | Yes  | Type of data to return.|

**ArkTS example**

```ts
import { Sensor, HeartRateResponse, SubscribeHeartRateOptions } from '@kit.SensorServiceKit';

let subscribeHeartRateOptions: SubscribeHeartRateOptions = {
  success: (ret: HeartRateResponse) => {
    console.info('Succeeded in subscribing. Get heartRate value:' + ret.heartRate);
  },
  fail: (data: string, code: number) => {
    console.error(`Failed to subscribe. Code: ${code}, data: ${data}`);
  },
};
Sensor.subscribeHeartRate(subscribeHeartRateOptions);
```

**JS example**

```js
import Sensor from '@system.sensor';

let subscribeHeartRateOptions = {
  success: (ret) => {
    console.info('Succeeded in subscribing. Get heartRate value:' + ret.heartRate);
  },
  fail: (data, code) => {
    console.error(`Failed to subscribe. Code: ${code}, data: ${data}`);
  },
};
sensor.subscribeHeartRate(subscribeHeartRateOptions);
```


### Sensor.unsubscribeHeartRate

static unsubscribeHeartRate(): void

Unsubscribes from data of the heart rate sensor. After this method is called, the callback for the heart rate sensor will not be triggered.

Call this method to cancel the subscription when the heart rate data is no longer needed.

After this method is called, the callback function registered using **subscribeHeartRate** will not be triggered. You need to call **subscribeHeartRate** to register to the callback before calling this method for unsubscription. Otherwise, this method will not take effect.

> **NOTE**
>
> For devices other than lite wearables, you are advised to use [HEART_RATE](js-apis-sensor.md#sensoroffsensortypesensor_type_id_heart_ratedeprecated) instead since API version 8.

**System capability**: SystemCapability.Sensors.Sensor.Lite

**Required permissions**: ohos.permission.READ_HEALTH_DATA

**ArkTS example**

```ts
Sensor.unsubscribeHeartRate();
```

**JS example**

```js
Sensor.unsubscribeHeartRate();
```

### Sensor.subscribeOnBodyState

 static subscribeOnBodyState(options: SubscribeOnBodyStateOptions): void

Subscribes to device wear status changes. Obtains the device wear status through a callback function. The data is in the format of a **OnBodyStateResponse** object, which contains the **value** field (boolean type).

This API can be used to check whether a wearable device is being worn by a user, so as to implement functions such as wear status detection and automatic start/stop.

After this API is called, the system reports data when the wear status changes. If this API is called multiple times for the same app, the last call takes effect.

> **NOTE**
>
> For devices other than lite wearables, you are advised to use [WEAR_DETECTION](js-apis-sensor.md#sensoronsensortypesensor_type_id_wear_detectiondeprecated) instead since API version 8.

**System capability**: SystemCapability.Sensors.Sensor.Lite

**Parameters**

| Name | Type                                                       | Mandatory| Description                  |
| ------- | ----------------------------------------------------------- | ---- | ---------------------- |
| options | [SubscribeOnBodyStateOptions](#subscribeonbodystateoptions) | Yes  | Called when the wear status changes.|

**ArkTS example**

```ts
import { Sensor, OnBodyStateResponse, SubscribeOnBodyStateOptions } from '@kit.SensorServiceKit';

let subscribeOnBodyStateOptions: SubscribeOnBodyStateOptions = {
  success: (ret: OnBodyStateResponse) => {
    console.info('Succeeded in subscribing. Get on-body state value:' + ret.value);
  },
  fail: (data: string, code: number) => {
    console.error(`Failed to subscribe. Code: ${code}, data: ${data}`);
  },
};
Sensor.subscribeOnBodyState(subscribeOnBodyStateOptions);
```

**JS example**

```js
import Sensor from '@system.sensor';

let subscribeOnBodyStateOptions = {
  success: (ret) => {
    console.info('Succeeded in subscribing. Get on-body state value:' + ret.value);
  },
  fail: (data, code) => {
    console.error(`Failed to subscribe. Code: ${code}, data: ${data}`);
  },
};
sensor.subscribeOnBodyState(subscribeOnBodyStateOptions);
```

### Sensor.unsubscribeOnBodyState

static unsubscribeOnBodyState(): void

Unsubscribes from wearing status changes of a wearable device. After this method is called, the callback for wearing status changes will not be triggered.

When the wearing status data is no longer needed, call this method to cancel the subscription.

After this method is called, the callback registered using **subscribeOnBodyState** will not be triggered. You need to call **subscribeOnBodyState** to register to the callback before calling this method for unsubscription. Otherwise, this method will not take effect.

> **NOTE**
>
> For devices other than lite wearables, you are advised to use [WEAR_DETECTION](js-apis-sensor.md#sensoroffsensortypesensor_type_id_wear_detectiondeprecated) instead since API version 8.

**System capability**: SystemCapability.Sensors.Sensor.Lite

**ArkTS example**

```ts
Sensor.unsubscribeOnBodyState();
```

**JS example**

```js
Sensor.unsubscribeOnBodyState();
```

### Sensor.getOnBodyState

 static getOnBodyState(options: GetOnBodyStateOptions): void

Obtains the wearing state of a wearable device. This API is used to obtain the wearing state at a time, which is different from the continuous subscription mode of **subscribeOnBodyState**. Only the wearing state at the current time is returned.

Use this API when you need to obtain the current wearing state of a wearable device at a time (rather than continuously listening to changes).

After this API is called, the system returns the current wearing state through the **success** callback. This API does not continuously report data and returns the result only once.

> **NOTE**
>
> For devices other than lite wearables, you are advised to use [WEAR_DETECTION](js-apis-sensor.md#sensoronsensortypesensor_type_id_wear_detectiondeprecated) instead since API version 8.

**System capability**: SystemCapability.Sensors.Sensor.Lite

**Parameters**

| Name | Type                                           | Mandatory| Description                      |
| ------- | ----------------------------------------------- | ---- | -------------------------- |
| options | [GetOnBodyStateOptions](#getonbodystateoptions) | Yes  | Callback invoked when obtaining the wearing state of the device that houses the sensor.|

**ArkTS example**

```ts
import { Sensor, OnBodyStateResponse, GetOnBodyStateOptions } from '@kit.SensorServiceKit';

let getOnBodyStateOptions: GetOnBodyStateOptions = {
  success: (ret: OnBodyStateResponse) => {
    console.info('Succeeded in getting. On body state: ' + ret.value);
  },
  fail: (data: string, code: number) => {
    console.error(`Failed to subscribe. Code: ${code}, data: ${data}`);
  },
};
Sensor.getOnBodyState(getOnBodyStateOptions);
```

**JS example**

```js
import Sensor from '@system.sensor';

let getOnBodyStateOptions = {
  success: (ret) => {
    console.info('Succeeded in getting. On body state: ' + ret.value);
  },
  fail: (data, code) => {
    console.error(`Failed to subscribe. Code: ${code}, data: ${data}`);
  },
};
sensor.getOnBodyState(getOnBodyStateOptions);
```

### Sensor.subscribeDeviceOrientation<sup>6+</sup>

 static subscribeDeviceOrientation(options: SubscribeDeviceOrientationOptions): void

Subscribes to data changes of the device orientation sensor. The device orientation data is obtained through a callback function. The data is in the format of a **DeviceOrientationResponse** object, which contains the **alpha**, **beta**, and **gamma** rotation angles (unit: degree).

This API can be used when you need to obtain the device orientation information to implement functions such as screen rotation, game direction control, and AR/VR scenarios.

If this API is called multiple times for the same app, the last call takes effect. However, this API cannot be called multiple times in one click event.

> **NOTE**
>
> For devices other than lite wearables, you are advised to use [ORIENTATION](js-apis-sensor.md#sensoronsensortypesensor_type_id_orientationdeprecated) instead since API version 8.

**System capability**: SystemCapability.Sensors.Sensor.Lite

**Device behavior differences**: This API can be called on wearables and lite wearables, but has no effect on other device types.

**Parameters**

| Name | Type                                                        | Mandatory| Description                                            |
| ------- | ------------------------------------------------------------ | ---- | ------------------------------------------------ |
| options | [SubscribeDeviceOrientationOptions](#subscribedeviceorientationoptions6) | Yes  | Sets the parameters for subscribing to the device orientation sensor, including the callback frequency and callback function.|

**ArkTS example**

```ts
import { Sensor, DeviceOrientationResponse, SubscribeDeviceOrientationOptions } from '@kit.SensorServiceKit';

let subscribeDeviceOrientationOptions: SubscribeDeviceOrientationOptions = {
  interval: 'normal',
  success: (ret: DeviceOrientationResponse) => {
    console.info('Succeeded in subscribing. Alpha data: ' + ret.alpha);
    console.info('Succeeded in subscribing. Beta data: ' + ret.beta);
    console.info('Succeeded in subscribing. Gamma data: ' + ret.gamma);
  },
  fail: (data: string, code: number) => {
    console.error(`Failed to subscribe. Code: ${code}, data: ${data}`);
  }
};
Sensor.subscribeDeviceOrientation(subscribeDeviceOrientationOptions);
```

**JS example**

```js
import Sensor from '@system.sensor';

let subscribeDeviceOrientationOptions = {
  interval: 'normal',
  success: (ret) => {
    console.info('Succeeded in subscribing. Alpha data: ' + ret.alpha);
    console.info('Succeeded in subscribing. Beta data: ' + ret.beta);
    console.info('Succeeded in subscribing. Gamma data: ' + ret.gamma);
  },
  fail: (data, code) => {
    console.error(`Failed to subscribe. Code: ${code}, data: ${data}`);
  }
};
sensor.subscribeDeviceOrientation(subscribeDeviceOrientationOptions);
```

### Sensor.unsubscribeDeviceOrientation<sup>6+</sup>

static unsubscribeDeviceOrientation(): void

Unsubscribes from data changes of the device orientation sensor. After this method is called, the callback for the device orientation sensor will not be triggered.

When the device orientation data is no longer needed, call this method to cancel the subscription.

After this method is called, the callback registered using **subscribeDeviceOrientation** will not be triggered. You need to call **subscribeDeviceOrientation** to register to the callback before calling this method for unsubscription. Otherwise, this method will not take effect.

> **NOTE**
>
> For devices other than lite wearables, you are advised to use [ORIENTATION](js-apis-sensor.md#sensoroffsensortypesensor_type_id_orientationdeprecated) instead since API version 8.

**System capability**: SystemCapability.Sensors.Sensor.Lite

**Device behavior differences**: This API can be called on wearables and lite wearables, but has no effect on other device types.

**ArkTS example**

```ts
Sensor.unsubscribeDeviceOrientation();
```

**JS example**

```js
Sensor.unsubscribeDeviceOrientation();
```

### Sensor.subscribeGyroscope<sup>6+</sup>

 static subscribeGyroscope(options: SubscribeGyroscopeOptions): void

Subscribes to data changes of the gyroscope sensor. Obtains the rotational angular velocity data of the device along the x, y, and z axes through the callback function. The data is in the format of a **GyroscopeResponse** object, which contains three number field of **x**, **y**, and **z**. The unit is rad/s.

This API can be used to obtain the rotational angular velocity of a device to implement functions such as hand gesture recognition, game control, and posture tracking.

If this API is called multiple times for the same app, the last call takes effect. However, this API cannot be called multiple times in one click event.

> **NOTE**
>
> For devices other than lite wearables, you are advised to use [GYROSCOPE](js-apis-sensor.md#sensoronsensortypesensor_type_id_gyroscopedeprecated) instead since API version 8.

**System capability**: SystemCapability.Sensors.Sensor.Lite

**Required permissions**: ohos.permission.GYROSCOPE

**Parameters**

| Name | Type                                                    | Mandatory| Description                                          |
| ------- | -------------------------------------------------------- | ---- | ---------------------------------------------- |
| options | [SubscribeGyroscopeOptions](#subscribegyroscopeoptions6) | Yes  | Parameters for gyroscope sensor subscription, including the callback frequency and callback function.|

**ArkTS example**

```ts
import { Sensor, GyroscopeResponse, SubscribeGyroscopeOptions } from '@kit.SensorServiceKit';

let subscribeGyroscopeOptions: SubscribeGyroscopeOptions = {
  interval: 'normal',
  success: (ret: GyroscopeResponse) => {
    console.info('Succeeded in subscribing. X-axis data: ' + ret.x);
    console.info('Succeeded in subscribing. Y-axis data: ' + ret.y);
    console.info('Succeeded in subscribing. Z-axis data: ' + ret.z);
  },
  fail: (data: string, code: number) => {
    console.error(`Failed to subscribe. Code: ${code}, data: ${data}`);
  }
};
Sensor.subscribeGyroscope(subscribeGyroscopeOptions);
```

**JS example**

```js
import Sensor from '@system.sensor';

let subscribeGyroscopeOptions = {
  interval: 'normal',
  success: (ret) => {
    console.info('Succeeded in subscribing. X-axis data: ' + ret.x);
    console.info('Succeeded in subscribing. Y-axis data: ' + ret.y);
    console.info('Succeeded in subscribing. Z-axis data: ' + ret.z);
  },
  fail: (data, code) => {
    console.error(`Failed to subscribe. Code: ${code}, data: ${data}`);
  }
};
sensor.subscribeGyroscope(subscribeGyroscopeOptions);
```

### Sensor.unsubscribeGyroscope<sup>6+</sup>

static unsubscribeGyroscope(): void

Unsubscribes from data changes of the gyroscope sensor. After this method is called, the callback for the gyroscope sensor will not be triggered.

When the gyroscope sensor data is no longer needed, call this method to cancel the subscription.

After this method is called, the callback function registered using **subscribeGyroscope** will not be triggered. You need to call **subscribeGyroscope** to register the callback before calling this method for unsubscription. Otherwise, this method will not take effect.

> **NOTE**
>
> For devices other than lite wearables, you are advised to use [GYROSCOPE](js-apis-sensor.md#sensoroffsensortypesensor_type_id_gyroscopedeprecated) instead since API version 8.
**System capability**: SystemCapability.Sensors.Sensor.Lite

**Required permissions**: ohos.permission.GYROSCOPE

**ArkTS example**

```ts
Sensor.unsubscribeGyroscope();
```

**JS example**

```js
Sensor.unsubscribeGyroscope();
```

## subscribeAccelerometerOptions

Sets the parameters for subscribing to the acceleration sensor, including the callback frequency and callback function.

**System capability**: SystemCapability.Sensors.Sensor.Lite

**Required permissions**: ohos.permission.ACCELEROMETER

| Name    | Type                                           | Read-Only| Optional| Description                                                        |
| -------- | ----------------------------------------------- | ---- | ---- | ------------------------------------------------------------ |
| interval | string                                          | No  | No  | Execution frequency of the callback for returning the acceleration sensor data.<br>Default value: **'normal'**<br>Possible values:<br>- **'game'**: called at an interval of 20 ms, which is applicable to gaming scenarios.<br>- **'ui'**: called at an interval of 60 ms, which is applicable to UI updating scenarios.<br>- **'normal'**: called at an interval of 200 ms, which is applicable to power-saving scenarios.|
| success  | [AccelerometerResponse](#accelerometerresponse) | No  | No  | Callback function invoked when the acceleration sensor data changes. The callback parameter is an **AccelerometerResponse** object.                        |
| fail     | Function                                        | No  | Yes  | Callback invoked when an API call fails. The callback parameters are **data** of the string type and **code** of the number type, where **data** indicates the error information and **code** indicates the error code. If this parameter is not specified, no callback notification is sent when the API call fails.                                    |

## AccelerometerResponse 

Callback invoked when the acceleration sensor data changes. The callback returns the acceleration data of the device on the x, y, and z axes.

**System capability**: SystemCapability.Sensors.Sensor.Lite

**Required permissions**: ohos.permission.ACCELEROMETER

| Name| Type  | Read-Only| Optional| Description                                                      |
| ---- | ------ | ---- | ---- | ---------------------------------------------------------- |
| x    | number | No  | No  | Acceleration along the x-axis of the device, in m/s². Value range: The value is the actually reported physical quantity, which is determined by the hardware sensor.|
| y    | number | No  | No  | Acceleration along the y-axis of the device, in m/s². Value range: The value is the actually reported physical quantity, which is determined by the hardware sensor.|
| z    | number | No  | No  | Acceleration along the z-axis of the device, in m/s². Value range: The value is the actually reported physical quantity, which is determined by the hardware sensor. The acceleration along the z-axis is about 9.8 m/s² (gravity acceleration) when the device is still.|

## SubscribeCompassOptions

Sets the parameters for subscribing to the compass sensor, including the callback function.

**System capability**: SystemCapability.Sensors.Sensor.Lite

| Name   | Type                               | Read-Only| Optional| Description                          |
| ------- | ----------------------------------- | ---- | ---- | ------------------------------ |
| success | [CompassResponse](#compassresponse) | No  | No  | Callback invoked when the compass sensor data changes. The callback parameter is a **CompassResponse** object.|
| fail    | Function                            | No  | Yes  | Callback invoked when an API call fails. The callback parameters are **data** of the string type and **code** of the number type, where **data** indicates the error information and **code** indicates the error code. If this parameter is not specified, no callback notification is sent when the API call fails.      |

## CompassResponse 

Callback function response object after the compass data changes, including the degree of the direction that the device faces.

**System capability**: SystemCapability.Sensors.Sensor.Lite

| Name     | Type  | Read-Only| Optional| Description                |
| --------- | ------ | ---- | ---- | -------------------- |
| direction | number | No  | No  | Direction of the device, in degrees. The value range is [0, 360). The value **0** indicates north. The value is equal to the reported physical quantity.|

## SubscribeProximityOptions

Sets the parameters for subscribing to the distance sensor, including the callback function.

**System capability**: SystemCapability.Sensors.Sensor.Lite

**Device behavior differences**: This API can be called on wearables and lite wearables, but has no effect on other device types.

| Name   | Type                                   | Read-Only| Optional| Description                              |
| ------- | --------------------------------------- | ---- | ---- | ---------------------------------- |
| success | [ProximityResponse](#proximityresponse) | No  | No  | Callback function invoked when the proximity sensor data changes. The callback parameter is a **ProximityResponse** object.|
| fail    | Function                                | No  | Yes  | Callback invoked when an API call fails. The callback parameters are **data** of the string type and **code** of the number type, where **data** indicates the error information and **code** indicates the error code. If this parameter is not specified, no callback notification is sent when the API call fails.          |

## ProximityResponse 

Callback function response object after the proximity sensor data changes, including the distance between a visible object and the device screen.

**System capability**: SystemCapability.Sensors.Sensor.Lite

**Device behavior differences**: This API can be called on wearables and lite wearables, but has no effect on other device types.

| Name    | Type  | Read-Only| Optional| Description                                      |
| -------- | ------ | ---- | ---- | ------------------------------------------ |
| distance | number | No  | No  | Distance between a visible object and the device screen. Value range: **0** indicates that the object is close to the screen (near state), and a value greater than 0 indicates that the object is far away from the screen (far state). The specific value of the far state is determined by the hardware sensor.|

## SubscribeLightOptions

Sets the parameters for subscribing to the ambient light sensor, including the callback function.

**System capability**: SystemCapability.Sensors.Sensor.Lite

**Device behavior differences**: This API can be called on wearables and lite wearables, but has no effect on other device types.

| Name   | Type                           | Read-Only| Optional| Description                          |
| ------- | ------------------------------- | ---- | ---- | ------------------------------ |
| success | [LightResponse](#lightresponse) | No  | No  | Callback function invoked when the ambient light sensor data changes. The callback parameter is a **LightResponse** object.|
| fail    | Function                        | No  | Yes  | Callback invoked when an API call fails. The callback parameters are **data** of the string type and **code** of the number type, where **data** indicates the error information and **code** indicates the error code. If this parameter is not specified, no callback notification is sent when the API call fails.      |

## LightResponse 

Callback invoked when the ambient light sensor data changes. The response object contains the ambient light intensity data.

**System capability**: SystemCapability.Sensors.Sensor.Lite

**Device behavior differences**: This API can be called on wearables and lite wearables, but has no effect on other device types.

| Name     | Type  | Read-Only| Optional| Description                 |
| --------- | ------ | ---- | ---- | --------------------- |
| intensity | number | No  | No  | Ambient light intensity, in lux. Value range: The value is the actually reported physical quantity, which is determined by the hardware sensor.|

## SubscribeStepCounterOptions

Sets the parameters for subscribing to the step counter sensor, including the callback function.

**Required permissions**: ohos.permission.ACTIVITY_MOTION

**System capability**: SystemCapability.Sensors.Sensor.Lite

| Name   | Type                                       | Read-Only| Optional| Description                            |
| ------- | ------------------------------------------- | ---- | ---- | -------------------------------- |
| success | [StepCounterResponse](#stepcounterresponse) | No  | No  | Callback function invoked when the step counter sensor data changes. The callback parameter is a **StepCounterResponse** object.|
| fail    | Function                                    | No  | Yes  | Callback invoked when an API call fails. The callback parameters are **data** of the string type and **code** of the number type, where **data** indicates the error information and **code** indicates the error code. If this parameter is not specified, no callback notification is sent when the API call fails.        |

## StepCounterResponse 

Defines a response object of the callback function invoked when the step counter sensor data changes, including the accumulated step count recorded after the step counter sensor is restarted.

**Required permissions**: ohos.permission.ACTIVITY_MOTION

**System capability**: SystemCapability.Sensors.Sensor.Lite

| Name | Type  | Read-Only| Optional| Description                            |
| ----- | ------ | ---- | ---- | -------------------------------- |
| steps | number | No  | No  | Number of counted steps after the sensor is restarted. Value range: an integer greater than or equal to 0. The value is the actually reported physical quantity. The step count restarts from 0 after the sensor is restarted.|

## SubscribeBarometerOptions

Configures the parameters for subscribing to the barometric pressure sensor, including the callback function.

**System capability**: SystemCapability.Sensors.Sensor.Lite

| Name   | Type                                   | Read-Only| Optional| Description                            |
| ------- | --------------------------------------- | ---- | ---- | -------------------------------- |
| success | [BarometerResponse](#barometerresponse) | No  | No  | Callback invoked when the barometric pressure sensor data changes. The callback parameter is a **BarometerResponse** object.|
| fail    | Function                                | No  | Yes  | Callback invoked when an API call fails. The callback parameters are **data** of the string type and **code** of the number type, where **data** indicates the error information and **code** indicates the error code. If this parameter is not specified, no callback notification is sent when the API call fails.        |

## BarometerResponse 

Defines a response object of the callback function after the barometric pressure sensor data is changed, including the atmospheric pressure value.

**System capability**: SystemCapability.Sensors.Sensor.Lite

| Name    | Type  | Read-Only| Optional| Description                  |
| -------- | ------ | ---- | ---- | ---------------------- |
| pressure | number | No  | No  | Atmospheric pressure, in Pa. Value range: The value is the actually reported physical quantity, which is determined by the hardware sensor. The standard atmospheric pressure is about 101,325 Pa.|

## SubscribeHeartRateOptions

Configures the parameters for subscribing to the heart rate sensor, including the callback function. The callback frequency of heart rate data is fixed at 5 seconds per time and cannot be configured using the interval parameter.

**Required permissions**: ohos.permission.READ_HEALTH_DATA

**System capability**: SystemCapability.Sensors.Sensor.Lite

| Name   | Type                                   | Read-Only| Optional| Description                                           |
| ------- | --------------------------------------- | ---- | ---- | ----------------------------------------------- |
| success | [HeartRateResponse](#heartrateresponse) | No  | No  | Callback invoked when the heart rate sensor data changes. The callback parameter is a **HeartRateResponse** object. The callback frequency is fixed at 5 seconds.|
| fail    | Function                                | No  | Yes  | Callback invoked when an API call fails. The callback parameters are **data** of the string type and **code** of the number type, where **data** indicates the error information and **code** indicates the error code. If this parameter is not specified, no callback notification is sent when the API call fails.                       |

## HeartRateResponse 

Defines a response object of the callback function after the heart rate sensor data is changed, including the heart rate value.

**Required permissions**: ohos.permission.READ_HEALTH_DATA

**System capability**: SystemCapability.Sensors.Sensor.Lite

| Name     | Type  | Read-Only| Optional| Description    |
| --------- | ------ | ---- | ---- | -------- |
| heartRate | number | No  | No  | Heart rate, in bpm. Value range: The value is the actually reported physical quantity, which is determined by the hardware sensor. The resting heart rate of a normal adult ranges from 60 to 100 bpm.|

## SubscribeOnBodyStateOptions

Sets the parameters for subscribing to the device wearing status, including the callback function. The wearing status can be worn or not worn.

**System capability**: SystemCapability.Sensors.Sensor.Lite

| Name   | Type                                       | Read-Only| Optional| Description                      |
| ------- | ------------------------------------------- | ---- | ---- | -------------------------- |
| success | [OnBodyStateResponse](#onbodystateresponse) | No  | No  | Callback invoked when the wearing state of the device that houses the sensor is successfully obtained. The callback parameter is an **OnBodyStateResponse** object.|
| fail    | Function                                    | No  | Yes  | Callback invoked when an API call fails. The callback parameters are **data** of the string type and **code** of the number type, where **data** indicates the error information and **code** indicates the error code. If this parameter is not specified, no callback notification is sent when the API call fails.  |

## OnBodyStateResponse 

Defines a response object of the device wearing status, including the data indicating whether the device is worn.

**System capability**: SystemCapability.Sensors.Sensor.Lite

| Name | Type   | Read-Only| Optional| Description                                              |
| ----- | ------- | ---- | ---- | -------------------------------------------------- |
| value | boolean | No  | No  | Whether the device is worn The value **true** indicates that the device is worn, and the value **false** indicates that the device is not worn.|

## GetOnBodyStateOptions

Obtains the parameters when the sensor is worn, including the callback function. This API is used to obtain the wearing status at a time and does not continuously listen to status changes.

**System capability**: SystemCapability.Sensors.Sensor.Lite

| Name    | Type                                       | Read-Only| Optional| Description                    |
| -------- | ------------------------------------------- | ---- | ---- | ------------------------ |
| success  | [OnBodyStateResponse](#onbodystateresponse) | No  | No  | Callback invoked when the API call succeeds. The callback parameter is an **OnBodyStateResponse** object.|
| fail     | Function                                    | No  | Yes  | Callback invoked when an API call fails. The callback parameters are **data** of the string type and **code** of the number type, where **data** indicates the error information and **code** indicates the error code. If this parameter is not specified, no callback notification is sent when the API call fails.|
| complete | Function                                    | No  | Yes  | Callback invoked when the API call is complete. This callback will be executed regardless of whether the API call succeeds or fails. If this parameter is not specified, no callback notification is sent when the API call is complete.|

## SubscribeDeviceOrientationOptions<sup>6+</sup>

Sets the parameters for subscribing to the device orientation sensor, including the callback frequency and callback function.

**System capability**: SystemCapability.Sensors.Sensor.Lite

**Device behavior differences**: This API can be called on wearables and lite wearables, but has no effect on other device types.

| Name    | Type                                                    | Read-Only| Optional| Description                                                        |
| -------- | -------------------------------------------------------- | ---- | ---- | ------------------------------------------------------------ |
| interval | string                                                   | No  | No  | Interval at which the callback is invoked to return the device orientation sensor data.<br>Default value: **'normal'**<br>Possible values:<br>- **'game'**: called at an interval of 20 ms, which is applicable to gaming scenarios.<br>- **'ui'**: called at an interval of 60 ms, which is applicable to UI updating scenarios.<br>- **'normal'**: called at an interval of 200 ms, which is applicable to power-saving scenarios.|
| success  | [DeviceOrientationResponse](#deviceorientationresponse6) | No  | No  | Callback invoked when the device orientation sensor data changes. The callback parameter is a **DeviceOrientationResponse** object.                  |
| fail     | Function                                                 | No  | Yes  | Callback invoked when an API call fails. The callback parameters are **data** of the string type and **code** of the number type, where **data** indicates the error information and **code** indicates the error code. If this parameter is not specified, no callback notification is sent when the API call fails.                                    |

## DeviceOrientationResponse<sup>6+</sup> 

Defines a response object of the callback function after the device orientation sensor data changes, including the three rotation angles of the device.

**System capability**: SystemCapability.Sensors.Sensor.Lite

**Device behavior differences**: This API can be called on wearables and lite wearables, but has no effect on other device types.

| Name | Type  | Read-Only| Optional| Description                                                        |
| ----- | ------ | ---- | ---- | ------------------------------------------------------------ |
| alpha | number | No  | No  | Rotation angle around the Z axis when the X/Y axis of the device coincides with the X/Y axis of the eart, in degrees. Value range: [0, 360]|
| beta  | number | No  | No  | Rotation angle around the X axis when the Y/Z axis of the device coincides with the Y/Z axis of the earth. in degrees. The value range is [-180, 180].|
| gamma | number | No  | No  | Rotation angle around the Y axis when the X/Z axis of the device coincides with the X/Z axis of the earth. in degrees. The value range is [-90, 90].|

## SubscribeGyroscopeOptions<sup>6+</sup> 

Defines the parameters for subscribing to the gyroscope sensor, including the callback frequency and callback function.

**Required permissions**: ohos.permission.GYROSCOPE

**System capability**: SystemCapability.Sensors.Sensor.Lite

| Name    | Type                                    | Read-Only| Optional| Description                                                        |
| -------- | ---------------------------------------- | ---- | ---- | ------------------------------------------------------------ |
| interval | string                                   | No  | No  | Interval at which the callback is invoked to return the gyroscope sensor data.<br>Default value: **'normal'**<br>Possible values:<br>- **'game'**: called at an interval of 20 ms, which is applicable to gaming scenarios.<br>- **'ui'**: called at an interval of 60 ms, which is applicable to UI updating scenarios.<br>- **'normal'**: called at an interval of 200 ms, which is applicable to power-saving scenarios.|
| success  | [GyroscopeResponse](#gyroscoperesponse6) | No  | No  | Callback invoked when the gyroscope sensor data changes. The callback parameter is a **GyroscopeResponse** object.                          |
| fail     | Function                                 | No  | Yes  | Callback invoked when an API call fails. The callback parameters are **data** of the string type and **code** of the number type, where **data** indicates the error information and **code** indicates the error code. If this parameter is not specified, no callback notification is sent when the API call fails.                                    |

## GyroscopeResponse<sup>6+</sup> 

Defines a response object of the callback function after the gyroscope sensor data changes, including the rotational velocity data of the device on the x, y, and z axes.

**Required permissions**: ohos.permission.GYROSCOPE

**System capability**: SystemCapability.Sensors.Sensor.Lite

| Name| Type  | Read-Only| Optional| Description             |
| ---- | ------ | ---- | ---- | ----------------- |
| x    | number | No  | No  | Rotation angular velocity of the X axis, in rad/s. Value range: The value is the actually reported physical quantity, which is determined by the hardware sensor.|
| y    | number | No  | No  | Rotation angular velocity of the Y axis, in rad/s. Value range: The value is the actually reported physical quantity, which is determined by the hardware sensor.|
| z    | number | No  | No  | Rotation angular velocity of the Z axis, in rad/s. Value range: The value is the actually reported physical quantity, which is determined by the hardware sensor.|
