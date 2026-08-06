# @system.sensor (Sensor)
<!--Kit: Sensor Service Kit-->
<!--Subsystem: Sensors-->
<!--Owner: @dilligencer-->
<!--Designer: @andeszhang-->
<!--Tester: @liuhaonan2-->
<!--Adviser: @hu-zhiqiong-->

The **Sensor** module provides APIs for querying the sensor list, subscribing to or unsubscribing from sensor data, and executing control commands.

The sensors are classified into the following categories based on their functions: motion, environment, orientation, light, body, and other categories (such as Hall effect sensors). Each category includes different sensor types. A sensor type may be a single hardware sensor or a composite of multiple hardware sensors.


> **NOTE**
>
> - Module maintenance policy:
>     - For lite wearables, this module is constantly maintained and available.
>     - For other device types, this module is no longer maintained since API version 8, and you are advised to use the new [@ohos.sensor](js-apis-sensor.md) module.
> - The initial APIs of this module are supported since API version 3. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - This module requires hardware support and can only be debugged on real devices.


## Modules to Import


```ts
import { Sensor } from '@kit.SensorServiceKit';
```
## Sensor

### Sensor.subscribeAccelerometer

 static subscribeAccelerometer(options: subscribeAccelerometerOptions): void

Subscribes to data changes of the acceleration sensor. If this API is called multiple times for the same application, the last call takes effect.

> **NOTE**
>
> For devices other than lite wearables, you are advised to use [ACCELEROMETER](js-apis-sensor.md#sensoronsensortypesensor_type_id_accelerometerdeprecated) since API version 8.

**System capability**: SystemCapability.Sensors.Sensor.Lite

**Required permissions**: ohos.permission.ACCELEROMETER (a system permission)

**Parameters**

| Name | Type                                                        | Mandatory| Description                                      |
| ------- | ------------------------------------------------------------ | ---- | ------------------------------------------ |
| options | [subscribeAccelerometerOptions](#subscribeaccelerometeroptions) | Yes  | Type of data to return.|

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
              console.info(this.TAG + 'Succeeded in subscribing. On body state: ' + ret.value);
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
          sensor.unsubscribeProximity()
          break;
        case "AMBIENT_LIGHT":
          sensor.unsubscribeLight()
          break;
        case "PEDOMETER":
          sensor.unsubscribeStepCounter()
          break;
        case "BAROMETER":
          sensor.unsubscribeBarometer();
          break;
        case "HEART_RATE":
          sensor.unsubscribeHeartRate()
          break;
        case "WEAR_DETECTION":
          sensor.unsubscribeOnBodyState()
          break;
        case "ORIENTATION":
          sensor.unsubscribeDeviceOrientation();
          break;
        case "GYROSCOPE":
          sensor.unsubscribeGyroscope();
          break;
        }
        this.TextContent = ""
    } catch (e) {
        console.error(this.TAG + `unsubscribe exception occurred, code: ${e.code}, message: ${e.message}`)
    }
  }
}
```

> **NOTE**
> To reduce performance overhead, you are advised to unsubscribe from the sensor data in the **onDestroy** callback.

### Sensor.unsubscribeAccelerometer

unsubscribeAccelerometer(): void

Unsubscribes from data changes of the acceleration sensor.

> **NOTE**
>
> For devices other than lite wearables, you are advised to use [ACCELEROMETER](js-apis-sensor.md#sensoroffsensortypesensor_type_id_accelerometerdeprecated) since API version 8.

**System capability**: SystemCapability.Sensors.Sensor.Lite

**Required permissions**: ohos.permission.ACCELEROMETER (a system permission)

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

Subscribes to data changes of the compass sensor. If this API is called multiple times for the same application, the last call takes effect.

> **NOTE**
>
> For devices other than lite wearables, you are advised to use [ORIENTATION](js-apis-sensor.md#sensoronsensortypesensor_type_id_orientationdeprecated) since API version 8.

**System capability**: SystemCapability.Sensors.Sensor.Lite

**Parameters**

| Name | Type                                               | Mandatory| Description                            |
| ------- | --------------------------------------------------- | ---- | -------------------------------- |
| options | [SubscribeCompassOptions](#subscribecompassoptions) | Yes  | Type of data to return.|

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

> **NOTE**
> To reduce performance overhead, you are advised to unsubscribe from the sensor data in the **onDestroy** callback.

### Sensor.unsubscribeCompass

static unsubscribeCompass(): void

Unsubscribes from data changes of the compass sensor.

> **NOTE**
>
> For devices other than lite wearables, you are advised to use [ORIENTATION](js-apis-sensor.md#sensoroffsensortypesensor_type_id_orientationdeprecated) since API version 8.

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

Subscribes to data changes of the proximity sensor. If this API is called multiple times for the same application, the last call takes effect.

> **NOTE**
>
> For devices other than lite wearables, you are advised to use [PROXIMITY](js-apis-sensor.md#sensoronsensortypesensor_type_id_proximitydeprecated) since API version 8.

**System capability**: SystemCapability.Sensors.Sensor.Lite

**Device behavior differences**: This API has no effect on lite wearables, but works properly on other devices.

**Parameters**

| Name | Type                                                   | Mandatory| Description                            |
| ------- | ------------------------------------------------------- | ---- | -------------------------------- |
| options | [SubscribeProximityOptions](#subscribeproximityoptions) | Yes  | Type of data to return.|

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

> **NOTE**
> To reduce performance overhead, you are advised to unsubscribe from the sensor data in the **onDestroy** callback.

### Sensor.unsubscribeProximity

static unsubscribeProximity(): void

Unsubscribes from data changes of the proximity sensor.

> **NOTE**
>
> For devices other than lite wearables, you are advised to use [PROXIMITY](js-apis-sensor.md#sensoroffsensortypesensor_type_id_proximitydeprecated) since API version 8.

**System capability**: SystemCapability.Sensors.Sensor.Lite

**Device behavior differences**: This API has no effect on lite wearables, but works properly on other devices.

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

Subscribes to data changes of the ambient light sensor. If this API is called multiple times, the last call takes effect.

> **NOTE**
>
> For devices other than lite wearables, you are advised to use [AMBIENT_LIGHT](js-apis-sensor.md#sensoronsensortypesensor_type_id_ambient_lightdeprecated) since API version 8.

**System capability**: SystemCapability.Sensors.Sensor.Lite

**Device behavior differences**: This API has no effect on lite wearables, but works properly on other devices.

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

> **NOTE**
> To reduce performance overhead, you are advised to unsubscribe from the sensor data in the **onDestroy** callback.

### Sensor.unsubscribeLight

static unsubscribeLight(): void

Unsubscribes from data changes of the ambient light sensor.

> **NOTE**
>
> For devices other than lite wearables, you are advised to use [AMBIENT_LIGHT](js-apis-sensor.md#sensoroffsensortypesensor_type_id_ambient_lightdeprecated) instead since API version 8.

**System capability**: SystemCapability.Sensors.Sensor.Lite

**Device behavior differences**: This API has no effect on lite wearables, but works properly on other devices.

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

Subscribes to data changes of the step counter sensor. If this API is called multiple times for the same application, the last call takes effect.

> **NOTE**
>
> For devices other than lite wearables, you are advised to use [PEDOMETER](js-apis-sensor.md#sensoronsensortypesensor_type_id_pedometerdeprecated) since API version 8.

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

> **NOTE**
> To reduce performance overhead, you are advised to unsubscribe from the sensor data in the **onDestroy** callback.

### Sensor.unsubscribeStepCounter

static unsubscribeStepCounter(): void

Unsubscribes from data changes of the step counter sensor.

> **NOTE**
>
> For devices other than lite wearables, you are advised to use [PEDOMETER](js-apis-sensor.md#sensoroffsensortypesensor_type_id_pedometerdeprecated) since API version 8.

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

Subscribes to data changes of the barometer sensor. If this API is called multiple times for the same application, the last call takes effect.

> **NOTE**
>
> For devices other than lite wearables, you are advised to use [BAROMETER](js-apis-sensor.md#sensoronsensortypesensor_type_id_barometerdeprecated) since API version 8.

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

> **NOTE**
> To reduce performance overhead, you are advised to unsubscribe from the sensor data in the **onDestroy** callback.


### Sensor.unsubscribeBarometer

static unsubscribeBarometer(): void

Unsubscribes from data changes of the barometer sensor.

> **NOTE**
>
> For devices other than lite wearables, you are advised to use [BAROMETER](js-apis-sensor.md#sensoroffsensortypesensor_type_id_barometerdeprecated) since API version 8.

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

Subscribes to data changes of the heart rate sensor. If this API is called multiple times for the same application, the last call takes effect.

> **NOTE**
>
> For devices other than lite wearables, you are advised to use [HEART_RATE](js-apis-sensor.md#sensoronsensortypesensor_type_id_heart_ratedeprecated) since API version 8.

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

> **NOTE**
> To reduce performance overhead, you are advised to unsubscribe from the sensor data in the **onDestroy** callback.


### Sensor.unsubscribeHeartRate

static unsubscribeHeartRate(): void

Unsubscribes from data changes of the heart rate sensor.

> **NOTE**
>
> For devices other than lite wearables, you are advised to use [HEART_RATE](js-apis-sensor.md#sensoroffsensortypesensor_type_id_heart_ratedeprecated) since API version 8.

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

Subscribes to wearing status changes of a wearable device. If this API is called multiple times for the same application, the last call takes effect.

> **NOTE**
>
> For devices other than lite wearables, you are advised to use [WEAR_DETECTION](js-apis-sensor.md#sensoronsensortypesensor_type_id_wear_detectiondeprecated) since API version 8.

**System capability**: SystemCapability.Sensors.Sensor.Lite

**Parameters**

| Name | Type                                                       | Mandatory| Description                  |
| ------- | ----------------------------------------------------------- | ---- | ---------------------- |
| options | [SubscribeOnBodyStateOptions](#subscribeonbodystateoptions) | Yes  | Type of data to return.|

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

> **NOTE**
> To reduce performance overhead, you are advised to unsubscribe from the sensor data in the **onDestroy** callback.

### Sensor.unsubscribeOnBodyState

static unsubscribeOnBodyState(): void

Unsubscribes from wearing status changes of a wearable device.

> **NOTE**
>
> For devices other than lite wearables, you are advised to use [WEAR_DETECTION](js-apis-sensor.md#sensoroffsensortypesensor_type_id_wear_detectiondeprecated) since API version 8.

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

Obtains the wearing state of a wearable device.

> **NOTE**
>
> For devices other than lite wearables, you are advised to use [WEAR_DETECTION](js-apis-sensor.md#sensoronsensortypesensor_type_id_wear_detectiondeprecated) since API version 8.

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
    console.info('Succeeded in subscribing. On body state: ' + ret.value);
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
    console.info('Succeeded in subscribing. On body state: ' + ret.value);
  },
  fail: (data, code) => {
    console.error(`Failed to subscribe. Code: ${code}, data: ${data}`);
  },
};
sensor.getOnBodyState(getOnBodyStateOptions);
```

### Sensor.subscribeDeviceOrientation<sup>6+</sup>

 static subscribeDeviceOrientation(options: SubscribeDeviceOrientationOptions): void

Subscribes to data changes of the device orientation sensor.

If this API is called multiple times for the same application, the last call takes effect. However, this API cannot be called multiple times in one click event.

> **NOTE**
>
> For devices other than lite wearables, you are advised to use [ORIENTATION](js-apis-sensor.md#sensoronsensortypesensor_type_id_orientationdeprecated) since API version 8.

**System capability**: SystemCapability.Sensors.Sensor.Lite

**Device behavior differences**: This API has no effect on lite wearables, but works properly on other devices.

**Parameters**

| Name | Type                                                        | Mandatory| Description                                            |
| ------- | ------------------------------------------------------------ | ---- | ------------------------------------------------ |
| options | [SubscribeDeviceOrientationOptions](#subscribedeviceorientationoptions6) | Yes  | Type of data to return.|

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

> **NOTE**
> To reduce performance overhead, you are advised to unsubscribe from the sensor data in the **onDestroy** callback.

### Sensor.unsubscribeDeviceOrientation<sup>6+</sup>

static unsubscribeDeviceOrientation(): void

Unsubscribes from data changes of the device orientation sensor.

> **NOTE**
>
> For devices other than lite wearables, you are advised to use [ORIENTATION](js-apis-sensor.md#sensoroffsensortypesensor_type_id_orientationdeprecated) since API version 8.

**System capability**: SystemCapability.Sensors.Sensor.Lite

**Device behavior differences**: This API has no effect on lite wearables, but works properly on other devices.

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

Subscribes to data changes of the gyroscope sensor.

If this API is called multiple times for the same application, the last call takes effect. However, this API cannot be called multiple times in one click event.

> **NOTE**
>
> For devices other than lite wearables, you are advised to use [GYROSCOPE](js-apis-sensor.md#sensoronsensortypesensor_type_id_gyroscopedeprecated) since API version 8.

**System capability**: SystemCapability.Sensors.Sensor.Lite

**Required permissions**: ohos.permission.GYROSCOPE (a system permission)

**Parameters**

| Name | Type                                                    | Mandatory| Description                                          |
| ------- | -------------------------------------------------------- | ---- | ---------------------------------------------- |
| options | [SubscribeGyroscopeOptions](#subscribegyroscopeoptions6) | Yes  | Type of data to return.|

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

> **NOTE**
> To reduce performance overhead, you are advised to unsubscribe from the sensor data in the **onDestroy** callback.

### Sensor.unsubscribeGyroscope<sup>6+</sup>

static unsubscribeGyroscope(): void

Unsubscribes from data changes of the gyroscope sensor.

> **NOTE**
>
> For devices other than lite wearables, you are advised to use [GYROSCOPE](js-apis-sensor.md#sensoroffsensortypesensor_type_id_gyroscopedeprecated) since API version 8.

**System capability**: SystemCapability.Sensors.Sensor.Lite

**Required permissions**: ohos.permission.GYROSCOPE (a system permission)

**ArkTS example**

```ts
Sensor.unsubscribeGyroscope();
```

**JS example**

```js
Sensor.unsubscribeGyroscope();
```

## subscribeAccelerometerOptions

Defines the type of data to return for a subscription to data changes of the acceleration sensor.

**System capability**: SystemCapability.Sensors.Sensor.Lite

**Required permissions**: ohos.permission.ACCELEROMETER

| Name    | Type                                           | Read-Only| Optional| Description                                                        |
| -------- | ----------------------------------------------- | ---- | ---- | ------------------------------------------------------------ |
| interval | string                                          | No  | No  | Execution frequency of the callback for returning the acceleration sensor data.<br>The default value is **normal**. The options are as follows:<br>- **game**: called at an interval of 20 ms, which is applicable to gaming scenarios.<br>- **ui**: called at an interval of 60 ms, which is applicable to UI updating scenarios.<br>- **normal**: called at an interval of 200 ms, which is applicable to power-saving scenarios.|
| success  | [AccelerometerResponse](#accelerometerresponse) | No  | No  | Callback invoked when the acceleration sensor data changes.                          |
| fail     | Function                                        | No  | Yes  | Callback invoked when an API call fails.                                    |

## AccelerometerResponse 

Defines the callback invoked when the acceleration sensor data changes. 

**System capability**: SystemCapability.Sensors.Sensor.Lite

**Required permissions**: ohos.permission.ACCELEROMETER

| Name| Type  | Read-Only| Optional| Description                                                      |
| ---- | ------ | ---- | ---- | ---------------------------------------------------------- |
| x    | number | No  | No  | Acceleration along the x-axis of the device, in m/s². The value is equal to the reported physical quantity.|
| y    | number | No  | No  | Acceleration along the y-axis of the device, in m/s². The value is equal to the reported physical quantity.|
| z    | number | No  | No  | Acceleration along the z-axis of the device, in m/s². The value is equal to the reported physical quantity.|

## SubscribeCompassOptions

Defines the type of data to return for a subscription to data changes of the compass sensor.

**System capability**: SystemCapability.Sensors.Sensor.Lite

| Name   | Type                               | Read-Only| Optional| Description                          |
| ------- | ----------------------------------- | ---- | ---- | ------------------------------ |
| success | [CompassResponse](#compassresponse) | No  | No  | Callback invoked when the compass sensor data changes.|
| fail    | Function                            | No  | Yes  | Callback invoked when an API call fails.      |

## CompassResponse 

Defines a **CompassResponse** object.

**System capability**: SystemCapability.Sensors.Sensor.Lite

| Name     | Type  | Read-Only| Optional| Description                |
| --------- | ------ | ---- | ---- | -------------------- |
| direction | number | No  | No  | Direction of the device, in degrees.|

## SubscribeProximityOptions

Defines the type of data to return for a subscription to data changes of the proximity sensor.

**System capability**: SystemCapability.Sensors.Sensor.Lite

**Device behavior differences**: This API has no effect on lite wearables, but works properly on other devices.

| Name   | Type                                   | Read-Only| Optional| Description                              |
| ------- | --------------------------------------- | ---- | ---- | ---------------------------------- |
| success | [ProximityResponse](#proximityresponse) | No  | No  | Defines a **ProximityResponse** object.|
| fail    | Function                                | No  | Yes  | Callback invoked when an API call fails.          |

## ProximityResponse 

Defines the callback invoked when the proximity sensor data changes.

**System capability**: SystemCapability.Sensors.Sensor.Lite

**Device behavior differences**: This API has no effect on lite wearables, but works properly on other devices.

| Name    | Type  | Read-Only| Optional| Description                                      |
| -------- | ------ | ---- | ---- | ------------------------------------------ |
| distance | number | No  | No  | Distance between a visible object and the device screen.|

## SubscribeLightOptions

Defines the type of data to return for a subscription to data changes of the ambient light sensor.

**System capability**: SystemCapability.Sensors.Sensor.Lite

**Device behavior differences**: This API has no effect on lite wearables, but works properly on other devices.

| Name   | Type                           | Read-Only| Optional| Description                          |
| ------- | ------------------------------- | ---- | ---- | ------------------------------ |
| success | [LightResponse](#lightresponse) | No  | No  | Callback invoked when the ambient light sensor data changes.|
| fail    | Function                        | No  | Yes  | Callback invoked when an API call fails.      |

## LightResponse 

Defines a **LightResponse** object.

**System capability**: SystemCapability.Sensors.Sensor.Lite

**Device behavior differences**: This API has no effect on lite wearables, but works properly on other devices.

| Name     | Type  | Read-Only| Optional| Description                 |
| --------- | ------ | ---- | ---- | --------------------- |
| intensity | number | No  | No  | Light intensity, in lux.|

## SubscribeStepCounterOptions

Defines the type of data to return for a subscription to data changes of the step counter sensor.

**Required permissions**: ohos.permission.ACTIVITY_MOTION

**System capability**: SystemCapability.Sensors.Sensor.Lite

| Name   | Type                                       | Read-Only| Optional| Description                            |
| ------- | ------------------------------------------- | ---- | ---- | -------------------------------- |
| success | [StepCounterResponse](#stepcounterresponse) | No  | No  | Defines a **StepCounterResponse** object.|
| fail    | Function                                    | No  | Yes  | Callback invoked when an API call fails.        |

## StepCounterResponse 

Defines the callback invoked when the step counter sensor data changes.

**Required permissions**: ohos.permission.ACTIVITY_MOTION

**System capability**: SystemCapability.Sensors.Sensor.Lite

| Name | Type  | Read-Only| Optional| Description                            |
| ----- | ------ | ---- | ---- | -------------------------------- |
| steps | number | No  | No  | Number of counted steps after the sensor is restarted.|

## SubscribeBarometerOptions

Defines the type of data to return for a subscription to data changes of the barometer sensor.

**System capability**: SystemCapability.Sensors.Sensor.Lite

| Name   | Type                                   | Read-Only| Optional| Description                            |
| ------- | --------------------------------------- | ---- | ---- | -------------------------------- |
| success | [BarometerResponse](#barometerresponse) | No  | No  | Callback invoked when the barometer sensor data changes.|
| fail    | Function                                | No  | Yes  | Callback invoked when an API call fails.        |

## BarometerResponse 

Defines a **BarometerResponse** object.

**System capability**: SystemCapability.Sensors.Sensor.Lite

| Name    | Type  | Read-Only| Optional| Description                  |
| -------- | ------ | ---- | ---- | ---------------------- |
| pressure | number | No  | No  | Pressure, in pascal.|

## SubscribeHeartRateOptions

Defines the type of data to return for a subscription to data changes of the heart rate sensor.

**Required permissions**: ohos.permission.READ_HEALTH_DATA

**System capability**: SystemCapability.Sensors.Sensor.Lite

| Name   | Type                                   | Read-Only| Optional| Description                                           |
| ------- | --------------------------------------- | ---- | ---- | ----------------------------------------------- |
| success | [HeartRateResponse](#heartrateresponse) | No  | No  | Callback invoked when the heart rate sensor data changes. This callback is invoked every five seconds.|
| fail    | Function                                | No  | Yes  | Callback invoked when an API call fails.                       |

## HeartRateResponse 

Defines a **HeartRateResponse** object.

**Required permissions**: ohos.permission.READ_HEALTH_DATA

**System capability**: SystemCapability.Sensors.Sensor.Lite

| Name     | Type  | Read-Only| Optional| Description    |
| --------- | ------ | ---- | ---- | -------- |
| heartRate | number | No  | No  | Heart rate.|

## SubscribeOnBodyStateOptions

Defines the callback invoked upon change in the wearing state of the device that houses the sensor.

**System capability**: SystemCapability.Sensors.Sensor.Lite

| Name   | Type                                       | Read-Only| Optional| Description                      |
| ------- | ------------------------------------------- | ---- | ---- | -------------------------- |
| success | [OnBodyStateResponse](#onbodystateresponse) | No  | No  | Callback invoked when the wearing state of the device that houses the sensor is successfully obtained.|
| fail    | Function                                    | No  | Yes  | Callback invoked when an API call fails.  |

## OnBodyStateResponse 

Specifies whether the device that houses the sensor is worn.

**System capability**: SystemCapability.Sensors.Sensor.Lite

| Name | Type   | Read-Only| Optional| Description                                              |
| ----- | ------- | ---- | ---- | -------------------------------------------------- |
| value | boolean | No  | No  | Boolean value indicating whether the device is worn. The value **true** indicates that the device is worn, and the value **false** indicates the opposite.|

## GetOnBodyStateOptions

 Defines the callback for obtaining the wearing state of the device that houses the sensor.

**System capability**: SystemCapability.Sensors.Sensor.Lite

| Name    | Type                                       | Read-Only| Optional| Description                    |
| -------- | ------------------------------------------- | ---- | ---- | ------------------------ |
| success  | [OnBodyStateResponse](#onbodystateresponse) | No  | No  | Callback upon a successful API call.|
| fail     | Function                                    | No  | Yes  | Callback invoked when an API call fails.|
| complete | Function                                    | No  | Yes  | Callback invoked when the API call is complete.|

## SubscribeDeviceOrientationOptions<sup>6+</sup>

Defines the type of data to return for a subscription to data changes of the device orientation sensor.

**System capability**: SystemCapability.Sensors.Sensor.Lite

**Device behavior differences**: This API has no effect on lite wearables, but works properly on other devices.

| Name    | Type                                                    | Read-Only| Optional| Description                                                        |
| -------- | -------------------------------------------------------- | ---- | ---- | ------------------------------------------------------------ |
| interval | string                                                   | No  | No  | Interval at which the callback is invoked to return the device orientation sensor data.<br>The default value is **normal**. The options are as follows:<br>- **game**: called at an interval of 20 ms, which is applicable to gaming scenarios.<br>- **ui**: called at an interval of 60 ms, which is applicable to UI updating scenarios.<br>- **normal**: called at an interval of 200 ms, which is applicable to power-saving scenarios.|
| success  | [DeviceOrientationResponse](#deviceorientationresponse6) | No  | No  | Callback invoked when the device orientation sensor data changes.                  |
| fail     | Function                                                 | No  | Yes  | Callback invoked when an API call fails.                                    |

## DeviceOrientationResponse<sup>6+</sup> 

Defines a **DeviceOrientationResponse** object.

**System capability**: SystemCapability.Sensors.Sensor.Lite

**Device behavior differences**: This API has no effect on lite wearables, but works properly on other devices.

| Name | Type  | Read-Only| Optional| Description                                                        |
| ----- | ------ | ---- | ---- | ------------------------------------------------------------ |
| alpha | number | No  | No  | Rotation angle around the Z axis when the X/Y axis of the device coincides with the X/Y axis of the earth.|
| beta  | number | No  | No  | Rotation angle around the X axis when the Y/Z axis of the device coincides with the Y/Z axis of the earth.|
| gamma | number | No  | No  | Rotation angle around the Y axis when the X/Z axis of the device coincides with the X/Z axis of the earth.|

## SubscribeGyroscopeOptions<sup>6+</sup> 

Defines the type of data to return for a subscription to data changes of the gyroscope sensor.

**Required permissions**: ohos.permission.GYROSCOPE

**System capability**: SystemCapability.Sensors.Sensor.Lite

| Name    | Type                                    | Read-Only| Optional| Description                                                        |
| -------- | ---------------------------------------- | ---- | ---- | ------------------------------------------------------------ |
| interval | string                                   | No  | No  | Interval at which the callback is invoked to return the gyroscope sensor data.<br>The default value is **normal**. The options are as follows:<br>- **game**: called at an interval of 20 ms, which is applicable to gaming scenarios.<br>- **ui**: called at an interval of 60 ms, which is applicable to UI updating scenarios.<br>- **normal**: called at an interval of 200 ms, which is applicable to power-saving scenarios.|
| success  | [GyroscopeResponse](#gyroscoperesponse6) | No  | No  | Callback invoked when the gyroscope sensor data changes.                          |
| fail     | Function                                 | No  | Yes  | Callback invoked when an API call fails.                                    |

## GyroscopeResponse<sup>6+</sup> 

Defines a **GyroscopeResponse** object.

**Required permissions**: ohos.permission.GYROSCOPE

**System capability**: SystemCapability.Sensors.Sensor.Lite

| Name| Type  | Read-Only| Optional| Description             |
| ---- | ------ | ---- | ---- | ----------------- |
| x    | number | No  | No  | Angular velocity of rotation around the x-axis of the device, in rad/s.|
| y    | number | No  | No  | Angular velocity of rotation around the y-axis of the device, in rad/s.|
| z    | number | No  | No  | Angular velocity of rotation around the z-axis of the device, in rad/s.|
