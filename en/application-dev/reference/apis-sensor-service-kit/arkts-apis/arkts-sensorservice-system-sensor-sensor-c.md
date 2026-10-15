# Sensor

```TypeScript
export default class Sensor
```

**Since:** 6

**Deprecated since:** 8

**Substitutes:** [sensor/sensor](arkts-sensorservice-sensor.md)

<!--Device-unnamed-export default class Sensor--><!--Device-unnamed-export default class Sensor-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite

## Modules to Import

```TypeScript
import { Sensor, AccelerometerResponse, BarometerResponse, CompassResponse, DeviceOrientationResponse, GetOnBodyStateOptions, GyroscopeResponse, HeartRateResponse, LightResponse, OnBodyStateResponse, ProximityResponse, StepCounterResponse, SubscribeBarometerOptions, SubscribeCompassOptions, SubscribeDeviceOrientationOptions, SubscribeGyroscopeOptions, SubscribeHeartRateOptions, SubscribeLightOptions, SubscribeOnBodyStateOptions, SubscribeProximityOptions, SubscribeStepCounterOptions, subscribeAccelerometerOptions } from '@kit.SensorServiceKit';
```

## getOnBodyState

```TypeScript
static getOnBodyState(options: GetOnBodyStateOptions): void
```

Obtains the wearing state of a wearable device. This API is used to obtain the wearing state at a time, which is different from the continuous subscription mode of **subscribeOnBodyState**. Only the wearing state at the current time is returned.

Use this API when you need to obtain the current wearing state of a wearable device at a time (rather than continuously listening to changes).

After this API is called, the system returns the current wearing state through the **success** callback. This API does not continuously report data and returns the result only once.

> **NOTE:** 
> 
> For devices other than lite wearables, you are advised to use
> [WEAR_DETECTION](arkts-sensorservice-sensor-on-f.md#on45)
> instead since API version 8.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [on](arkts-sensorservice-sensor-on-f.md#on45)(type: SensorType.SENSOR_TYPE_ID_WEAR_DETECTION, callback: Callback&lt;WearDetectionResponse&gt;, options?: Options)

**Model restriction:** This API can be used only in the FA model.

<!--Device-Sensor-static getOnBodyState(options: GetOnBodyStateOptions): void--><!--Device-Sensor-static getOnBodyState(options: GetOnBodyStateOptions): void-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [GetOnBodyStateOptions](arkts-sensorservice-system-sensor-getonbodystateoptions-i.md) | Yes | Callback invoked when obtaining the wearing state of the device that houses the sensor. |

## subscribeAccelerometer

```TypeScript
static subscribeAccelerometer(options: subscribeAccelerometerOptions): void
```

Subscribes to data changes of the acceleration sensor. Obtains the acceleration data of the device along the x, y, and z axes through a callback. The data is in the format of an **AccelerometerResponse** object, which contains three number fields of **x**, **y**, and **z**.

This API can be used to obtain the acceleration information of a device to implement functions such as motion detection and shake.

After this API is called, the system reports acceleration data at the specified callback frequency. If this API is called multiple times for the same app, the last call takes effect.

> **NOTE:** 
> 
> For devices other than lite wearables, you are advised to use
> [ACCELEROMETER](arkts-sensorservice-sensor-on-f.md#on25)
> instead since API version 8.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [on](arkts-sensorservice-sensor-on-f.md#on25)(type: SensorType.SENSOR_TYPE_ID_ACCELEROMETER, callback: Callback&lt;AccelerometerResponse&gt;, options?: Options)

**Required permissions:** ohos.permission.ACCELEROMETER

**Model restriction:** This API can be used only in the FA model.

<!--Device-Sensor-static subscribeAccelerometer(options: subscribeAccelerometerOptions): void--><!--Device-Sensor-static subscribeAccelerometer(options: subscribeAccelerometerOptions): void-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [subscribeAccelerometerOptions](arkts-sensorservice-system-sensor-subscribeaccelerometeroptions-i.md) | Yes | Parameters for subscribing to the acceleration sensor, including the callback frequency and callback function. |

## subscribeBarometer

```TypeScript
static subscribeBarometer(options: SubscribeBarometerOptions): void
```

Subscribes to data changes of the barometer sensor. The atmospheric pressure value is obtained through the callback function. The data is in the format of a **BarometerResponse** object, which contains the **pressure** field. The unit is Pa.

This API can be used to obtain the atmospheric pressure information to implement functions such as altitude estimation, weather monitoring, and indoor navigation.

After this API is called, the system reports data when the barometric pressure changes. If this API is called multiple times for the same app, the last call takes effect.

> **NOTE:** 
> 
> For devices other than lite wearables, you are advised to use
> [BAROMETER](arkts-sensorservice-sensor-on-f.md#on29)
> instead since API version 8.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [on](arkts-sensorservice-sensor-on-f.md#on29)(type: SensorType.SENSOR_TYPE_ID_BAROMETER, callback: Callback&lt;BarometerResponse&gt;, options?: Options)

**Model restriction:** This API can be used only in the FA model.

<!--Device-Sensor-static subscribeBarometer(options: SubscribeBarometerOptions): void--><!--Device-Sensor-static subscribeBarometer(options: SubscribeBarometerOptions): void-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [SubscribeBarometerOptions](arkts-sensorservice-system-sensor-subscribebarometeroptions-i.md) | Yes | Type of data to return. |

## subscribeCompass

```TypeScript
static subscribeCompass(options: SubscribeCompassOptions): void
```

Subscribes to data changes of the compass sensor. Obtains the device direction data through a callback. The data is in the format of a **CompassResponse object**, which contains the **direction** field.

This API can be used to obtain the device direction information to implement functions such as navigation and compass.

After this API is called, the system reports the device direction data when the compass data changes. If this API is called multiple times for the same app, the last call takes effect.

> **NOTE:** 
> 
> For devices other than lite wearables, you are advised to use
> [ORIENTATION](arkts-sensorservice-sensor-on-f.md#on39)
> instead since API Version 8.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [ORIENTATION](arkts-sensorservice-sensor-sensorid-e.md#orientation)

**Model restriction:** This API can be used only in the FA model.

<!--Device-Sensor-static subscribeCompass(options: SubscribeCompassOptions): void--><!--Device-Sensor-static subscribeCompass(options: SubscribeCompassOptions): void-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [SubscribeCompassOptions](arkts-sensorservice-system-sensor-subscribecompassoptions-i.md) | Yes | Type of data to return. |

## subscribeDeviceOrientation

```TypeScript
static subscribeDeviceOrientation(options: SubscribeDeviceOrientationOptions): void
```

Subscribes to data changes of the device orientation sensor. The device orientation data is obtained through a callback function. The data is in the format of a **DeviceOrientationResponse** object, which contains the **alpha**, **beta**, and **gamma** rotation angles (unit: degree).

This API can be used when you need to obtain the device orientation information to implement functions such as screen rotation, game direction control, and AR/VR scenarios.

If this API is called multiple times for the same app, the last call takes effect. However, this API cannot be called multiple times in one click event.

**Device behavior differences**: This API can be called on wearables and lite wearables, but has no effect on other device types.

> **NOTE:** 
> 
> For devices other than lite wearables, you are advised to use
> [ORIENTATION](arkts-sensorservice-sensor-on-f.md#on39)
> instead since API version 8.

**Since:** 6

**Deprecated since:** 8

**Substitutes:** [on](arkts-sensorservice-sensor-on-f.md#on39)(type: SensorType.SENSOR_TYPE_ID_ORIENTATION, callback: Callback&lt;OrientationResponse&gt;, options?: Options)

**Model restriction:** This API can be used only in the FA model.

<!--Device-Sensor-static subscribeDeviceOrientation(options: SubscribeDeviceOrientationOptions): void--><!--Device-Sensor-static subscribeDeviceOrientation(options: SubscribeDeviceOrientationOptions): void-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [SubscribeDeviceOrientationOptions](arkts-sensorservice-system-sensor-subscribedeviceorientationoptions-i.md) | Yes | Sets the parameters for subscribing to the device orientation sensor, including the callback frequency and callback function. |

## subscribeGyroscope

```TypeScript
static subscribeGyroscope(options: SubscribeGyroscopeOptions): void
```

Subscribes to data changes of the gyroscope sensor. Obtains the rotational angular velocity data of the device along the x, y, and z axes through the callback function. The data is in the format of a **GyroscopeResponse** object, which contains three number field of **x**, **y**, and **z**. The unit is rad/s.

This API can be used to obtain the rotational angular velocity of a device to implement functions such as hand gesture recognition, game control, and posture tracking.

If this API is called multiple times for the same app, the last call takes effect. However, this API cannot be called multiple times in one click event.

> **NOTE:** 
> 
> For devices other than lite wearables, you are advised to use
> [GYROSCOPE](arkts-sensorservice-sensor-on-f.md#on31)
> instead since API version 8.

**Since:** 6

**Deprecated since:** 8

**Substitutes:** [on](arkts-sensorservice-sensor-on-f.md#on31)(type: SensorType.SENSOR_TYPE_ID_GYROSCOPE, callback: Callback&lt;GyroscopeResponse&gt;, options?: Options)

**Required permissions:** ohos.permission.GYROSCOPE

**Model restriction:** This API can be used only in the FA model.

<!--Device-Sensor-static subscribeGyroscope(options: SubscribeGyroscopeOptions): void--><!--Device-Sensor-static subscribeGyroscope(options: SubscribeGyroscopeOptions): void-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [SubscribeGyroscopeOptions](arkts-sensorservice-system-sensor-subscribegyroscopeoptions-i.md) | Yes | Type of data to return. |

## subscribeHeartRate

```TypeScript
static subscribeHeartRate(options: SubscribeHeartRateOptions): void
```

Subscribes to data changes of the heart rate sensor. Obtains the heart rate data through the callback function. The data is in the format of a **HeartRateResponse** object, which contains the **heartRate** field. The unit is bpm. The default callback frequency is once every 5 seconds.

This API can be used to obtain the user's heart rate data to implement functions such as health monitoring and exercise intensity evaluation.

After this API is called, the system reports heart rate data every 5 seconds. If this API is called multiple times for the same app, the last call takes effect.

> **NOTE:** 
> 
> For devices other than lite wearables, you are advised to use
> [HEART_RATE](arkts-sensorservice-sensor-on-f.md#on34)
> instead since API version 8.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [on](arkts-sensorservice-sensor-on-f.md#on34)(type: SensorType.SENSOR_TYPE_ID_HEART_RATE, callback: Callback&lt;HeartRateResponse&gt;, options?: Options)

**Required permissions:** ohos.permission.READ_HEALTH_DATA

**Model restriction:** This API can be used only in the FA model.

<!--Device-Sensor-static subscribeHeartRate(options: SubscribeHeartRateOptions): void--><!--Device-Sensor-static subscribeHeartRate(options: SubscribeHeartRateOptions): void-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [SubscribeHeartRateOptions](arkts-sensorservice-system-sensor-subscribeheartrateoptions-i.md) | Yes | Type of data to return. |

## subscribeLight

```TypeScript
static subscribeLight(options: SubscribeLightOptions): void
```

Subscribes to ambient light sensor data changes. The ambient light intensity data is obtained through a callback function. The data is in the format of a **LightResponse** object, which contains the **intensity** field. The unit is lux.

This API is used when you need to obtain the ambient light intensity to implement functions such as automatic screen brightness adjustment and ambient light detection.

If this API is called multiple times, the last call takes effect.

**Device behavior differences**: This API can be called on wearables and lite wearables, but has no effect on other device types.

> **NOTE:** 
> 
> For devices other than lite wearables, you are advised to use
> [AMBIENT_LIGHT](arkts-sensorservice-sensor-on-f.md#on27)
> instead since API version 8.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [AMBIENT_LIGHT](arkts-sensorservice-sensor-sensorid-e.md#ambient_light)

**Model restriction:** This API can be used only in the FA model.

<!--Device-Sensor-static subscribeLight(options: SubscribeLightOptions): void--><!--Device-Sensor-static subscribeLight(options: SubscribeLightOptions): void-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [SubscribeLightOptions](arkts-sensorservice-system-sensor-subscribelightoptions-i.md) | Yes | Type of data to return. |

## subscribeOnBodyState

```TypeScript
static subscribeOnBodyState(options: SubscribeOnBodyStateOptions): void
```

Subscribes to device wear status changes. Obtains the device wear status through a callback function. The data is in the format of a **OnBodyStateResponse** object, which contains the **value** field (boolean type).

This API can be used to check whether a wearable device is being worn by a user, so as to implement functions such as wear status detection and automatic start/stop.

After this API is called, the system reports data when the wear status changes. If this API is called multiple times for the same app, the last call takes effect.

> **NOTE:** 
> 
> For devices other than lite wearables, you are advised to use
> [WEAR_DETECTION](arkts-sensorservice-sensor-on-f.md#on45)
> instead since API version 8.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [on](arkts-sensorservice-sensor-on-f.md#on45)(type: SensorType.SENSOR_TYPE_ID_WEAR_DETECTION, callback: Callback&lt;WearDetectionResponse&gt;, options?: Options)

**Model restriction:** This API can be used only in the FA model.

<!--Device-Sensor-static subscribeOnBodyState(options: SubscribeOnBodyStateOptions): void--><!--Device-Sensor-static subscribeOnBodyState(options: SubscribeOnBodyStateOptions): void-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [SubscribeOnBodyStateOptions](arkts-sensorservice-system-sensor-subscribeonbodystateoptions-i.md) | Yes | Called when the wear status changes. |

## subscribeProximity

```TypeScript
static subscribeProximity(options: SubscribeProximityOptions): void
```

Subscribes to data changes of the proximity sensor. Obtains the distance between a visible object and the device screen through the callback function. The data is in the format of the **ProximityResponse** object, which contains the **distance** field.

This API can be used to detect the distance between an object and the device screen to implement functions such as automatic screen-off during calls and mistouch prevention.

After this API is called, the system reports data when the data of the proximity sensor changes. If this API is called multiple times for the same app, only the last call takes effect.

**Device behavior differences**: This API can be called on wearables and lite wearables, but has no effect on other device types.

> **NOTE:** 
> 
> This API is supported since API version 3 and deprecated since API version 8.
> For devices other than lite wearables, you are advised to use
> [PROXIMITY](arkts-sensorservice-sensor-on-f.md#on42)
> instead.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [PROXIMITY](arkts-sensorservice-sensor-sensorid-e.md#proximity)

**Model restriction:** This API can be used only in the FA model.

<!--Device-Sensor-static subscribeProximity(options: SubscribeProximityOptions): void--><!--Device-Sensor-static subscribeProximity(options: SubscribeProximityOptions): void-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [SubscribeProximityOptions](arkts-sensorservice-system-sensor-subscribeproximityoptions-i.md) | Yes | Sets the parameters for subscribing to the distance sensor, including the callback function. |

## subscribeStepCounter

```TypeScript
static subscribeStepCounter(options: SubscribeStepCounterOptions): void
```

Subscribes to data changes of the step counter sensor. Callback function used to obtain the number of steps counted after the step counter sensor is restarted. The data is in the format of a **StepCounterResponse** object, which contains the steps field.

This API can be used to obtain the user's step count to implement functions such as step counting, fitness tracking, and health monitoring.

After this API is called, the system reports data when the step count data changes. If this API is called multiple times for the same app, the last call takes effect.

> **NOTE:** 
> 
> For devices other than lite wearables, you are advised to use
> [PEDOMETER](arkts-sensorservice-sensor-on-f.md#on40)
> instead since API version 8.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [on](arkts-sensorservice-sensor-on-f.md#on40)(type: SensorType.SENSOR_TYPE_ID_PEDOMETER, callback: Callback&lt;PedometerResponse&gt;, options?: Options)

**Required permissions:** ohos.permission.ACTIVITY_MOTION

**Model restriction:** This API can be used only in the FA model.

<!--Device-Sensor-static subscribeStepCounter(options: SubscribeStepCounterOptions): void--><!--Device-Sensor-static subscribeStepCounter(options: SubscribeStepCounterOptions): void-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [SubscribeStepCounterOptions](arkts-sensorservice-system-sensor-subscribestepcounteroptions-i.md) | Yes | Type of data to return. |

## unsubscribeAccelerometer

```TypeScript
static unsubscribeAccelerometer(): void
```

Unsubscribes from data of the acceleration sensor. After this method is called, the callback for the acceleration sensor will not be triggered.

When the acceleration sensor data is no longer needed (for example, when the page is switched or the app is exited), call this method to cancel the subscription to reduce system resource usage.

After this method is called, the callback registered using **subscribeAccelerometer** will not be triggered. To obtain data again, call **subscribeAccelerometer** again.

> **NOTE:** 
> 
> For devices other than lite wearables, you are advised to use
> [ACCELEROMETER](arkts-sensorservice-sensor-off-f.md#off48)
> instead since API version 8.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [off](arkts-sensorservice-sensor-off-f.md#off48)(type: SensorType.SENSOR_TYPE_ID_ACCELEROMETER, callback?: Callback&lt;AccelerometerResponse&gt;)

**Required permissions:** ohos.permission.ACCELEROMETER

**Model restriction:** This API can be used only in the FA model.

<!--Device-Sensor-static unsubscribeAccelerometer(): void--><!--Device-Sensor-static unsubscribeAccelerometer(): void-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite

## unsubscribeBarometer

```TypeScript
static unsubscribeBarometer(): void
```

Unsubscribes from data of the barometer sensor. After this method is called, the callback for the barometer sensor will not be triggered.

Call this method to cancel the subscription when the barometric pressure data is no longer needed.

After this method is called, the callback function registered using **subscribeBarometer** will not be triggered. You need to call **subscribeBarometer** to register to the callback before calling this method for unsubscription. Otherwise, this method will not take effect.

> **NOTE:** 
> 
> For devices other than lite wearables, you are advised to use
> [BAROMETER](arkts-sensorservice-sensor-off-f.md#off52)
> instead since API version 8.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [off](arkts-sensorservice-sensor-off-f.md#off52)(type: SensorType.SENSOR_TYPE_ID_BAROMETER, callback?: Callback&lt;BarometerResponse&gt;)

**Model restriction:** This API can be used only in the FA model.

<!--Device-Sensor-static unsubscribeBarometer(): void--><!--Device-Sensor-static unsubscribeBarometer(): void-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite

## unsubscribeCompass

```TypeScript
static unsubscribeCompass(): void
```

Unsubscribes from data of the compass sensor. After this method is called, the callback for the compass sensor will not be triggered.

Call this method to cancel the subscription when the compass sensor data is no longer needed.

After this method is called, the callback registered using **subscribeCompass** will not be triggered. You need to call **subscribeCompass** to register to the callback before calling this method for unsubscription. Otherwise, this method will not take effect.

> **NOTE:** 
> 
> For devices other than lite wearables, you are advised to use
> [ORIENTATION](arkts-sensorservice-sensor-off-f.md#off62)
> instead since API version 8.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [off](arkts-sensorservice-sensor-off-f.md#off62)(type: SensorType.SENSOR_TYPE_ID_ORIENTATION, callback?: Callback&lt;OrientationResponse&gt;)

**Model restriction:** This API can be used only in the FA model.

<!--Device-Sensor-static unsubscribeCompass(): void--><!--Device-Sensor-static unsubscribeCompass(): void-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite

## unsubscribeDeviceOrientation

```TypeScript
static unsubscribeDeviceOrientation(): void
```

Unsubscribes from data changes of the device orientation sensor. After this method is called, the callback for the device orientation sensor will not be triggered.

When the device orientation data is no longer needed, call this method to cancel the subscription.

After this method is called, the callback registered using **subscribeDeviceOrientation** will not be triggered. You need to call **subscribeDeviceOrientation** to register to the callback before calling this method for unsubscription. Otherwise, this method will not take effect.

**Device behavior differences**: This API can be called on wearables and lite wearables, but has no effect on other device types.

> **NOTE:** 
> 
> For devices other than lite wearables, you are advised to use
> [ORIENTATION](arkts-sensorservice-sensor-off-f.md#off62)
> instead since API version 8.

**Since:** 6

**Deprecated since:** 8

**Substitutes:** [off](arkts-sensorservice-sensor-off-f.md#off62)(type: SensorType.SENSOR_TYPE_ID_ORIENTATION, callback?: Callback&lt;OrientationResponse&gt;)

**Model restriction:** This API can be used only in the FA model.

<!--Device-Sensor-static unsubscribeDeviceOrientation(): void--><!--Device-Sensor-static unsubscribeDeviceOrientation(): void-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite

## unsubscribeGyroscope

```TypeScript
static unsubscribeGyroscope(): void
```

Unsubscribes from data changes of the gyroscope sensor. After this method is called, the callback for the gyroscope sensor will not be triggered.

When the gyroscope sensor data is no longer needed, call this method to cancel the subscription.

After this method is called, the callback function registered using **subscribeGyroscope** will not be triggered. You need to call **subscribeGyroscope** to register the callback before calling this method for unsubscription. Otherwise, this method will not take effect.

> **NOTE:** 
> 
> For devices other than lite wearables, you are advised to use
> [GYROSCOPE](arkts-sensorservice-sensor-off-f.md#off54)
> instead since API version 8.

**Since:** 6

**Deprecated since:** 8

**Substitutes:** [off](arkts-sensorservice-sensor-off-f.md#off54)(type: SensorType.SENSOR_TYPE_ID_GYROSCOPE, callback?: Callback&lt;GyroscopeResponse&gt;)

**Required permissions:** ohos.permission.GYROSCOPE

**Model restriction:** This API can be used only in the FA model.

<!--Device-Sensor-static unsubscribeGyroscope(): void--><!--Device-Sensor-static unsubscribeGyroscope(): void-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite

## unsubscribeHeartRate

```TypeScript
static unsubscribeHeartRate(): void
```

Unsubscribes from data of the heart rate sensor. After this method is called, the callback for the heart rate sensor will not be triggered.

Call this method to cancel the subscription when the heart rate data is no longer needed.

After this method is called, the callback function registered using **subscribeHeartRate** will not be triggered. You need to call **subscribeHeartRate** to register to the callback before calling this method for unsubscription. Otherwise, this method will not take effect.

> **NOTE:** 
> 
> For devices other than lite wearables, you are advised to use
> [HEART_RATE](arkts-sensorservice-sensor-off-f.md#off57)
> instead since API version 8.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [off](arkts-sensorservice-sensor-off-f.md#off57)(type: SensorType.SENSOR_TYPE_ID_HEART_RATE, callback?: Callback&lt;HeartRateResponse&gt;)

**Required permissions:** ohos.permission.READ_HEALTH_DATA

**Model restriction:** This API can be used only in the FA model.

<!--Device-Sensor-static unsubscribeHeartRate(): void--><!--Device-Sensor-static unsubscribeHeartRate(): void-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite

## unsubscribeLight

```TypeScript
static unsubscribeLight(): void
```

Unsubscribes from data of the ambient light sensor. After this method is called, the callback for the ambient light sensor will not be triggered.

When the ambient light sensor data is no longer needed, call this method to cancel the subscription.

After this method is called, the callback registered using **subscribeLight** will not be triggered. You need to call **subscribeLight** to register to the callback before calling this method for unsubscription. Otherwise, this method will not take effect.

**Device behavior differences**: This API can be called on wearables and lite wearables, but has no effect on other device types.

> **NOTE:** 
> 
> For devices other than lite wearables, you are advised to use
> [AMBIENT_LIGHT](arkts-sensorservice-sensor-off-f.md#off50)
> instead since API version 8.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [off](arkts-sensorservice-sensor-off-f.md#off50)(type: SensorType.SENSOR_TYPE_ID_AMBIENT_LIGHT, callback?: Callback&lt;LightResponse&gt;)

**Model restriction:** This API can be used only in the FA model.

<!--Device-Sensor-static unsubscribeLight(): void--><!--Device-Sensor-static unsubscribeLight(): void-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite

## unsubscribeOnBodyState

```TypeScript
static unsubscribeOnBodyState(): void
```

Unsubscribes from wearing status changes of a wearable device. After this method is called, the callback for wearing status changes will not be triggered.

When the wearing status data is no longer needed, call this method to cancel the subscription.

After this method is called, the callback registered using **subscribeOnBodyState** will not be triggered. You need to call **subscribeOnBodyState** to register to the callback before calling this method for unsubscription. Otherwise, this method will not take effect.

> **NOTE:** 
> 
> For devices other than lite wearables, you are advised to use
> [WEAR_DETECTION](arkts-sensorservice-sensor-off-f.md#off68)
> instead since API version 8.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [off](arkts-sensorservice-sensor-off-f.md#off68)(type: SensorType.SENSOR_TYPE_ID_WEAR_DETECTION, callback?: Callback&lt;WearDetectionResponse&gt;)

**Model restriction:** This API can be used only in the FA model.

<!--Device-Sensor-static unsubscribeOnBodyState(): void--><!--Device-Sensor-static unsubscribeOnBodyState(): void-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite

## unsubscribeProximity

```TypeScript
static unsubscribeProximity(): void
```

Unsubscribes from data of the distance sensor. After this method is called, the callback for the distance sensor will not be triggered.

When the distance sensor data is no longer needed, call this method to cancel the subscription.

After this method is called, the callback registered using **subscribeProximity** will not be triggered. You need to call **subscribeProximity** to register to the callback before calling this method for unsubscription. Otherwise, this method will not take effect.

**Device behavior differences**: This API can be called on wearables and lite wearables, but has no effect on other device types.

> **NOTE:** 
> 
> For devices other than lite wearables, you are advised to use
> [PROXIMITY](arkts-sensorservice-sensor-off-f.md#off65)
> instead since API version 8.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [PROXIMITY](arkts-sensorservice-sensor-sensorid-e.md#proximity)

**Model restriction:** This API can be used only in the FA model.

<!--Device-Sensor-static unsubscribeProximity(): void--><!--Device-Sensor-static unsubscribeProximity(): void-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite

## unsubscribeStepCounter

```TypeScript
static unsubscribeStepCounter(): void
```

Unsubscribes from data of the pedometer sensor. After this method is called, the callback for the pedometer sensor will not be triggered.

Call this method to cancel the subscription when the step count data is no longer needed.

After this method is called, the callback registered using **subscribeStepCounter** will not be triggered. You need to call **subscribeStepCounter** to register to the callback before calling this method for unsubscription. Otherwise, the unsubscription will not take effect.

> **NOTE:** 
> 
> For devices other than lite wearables, you are advised to use
> [PEDOMETER](arkts-sensorservice-sensor-off-f.md#off63)
> instead since API version 8.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [off](arkts-sensorservice-sensor-off-f.md#off63)(type: SensorType.SENSOR_TYPE_ID_PEDOMETER, callback?: Callback&lt;PedometerResponse&gt;)

**Required permissions:** ohos.permission.ACTIVITY_MOTION

**Model restriction:** This API can be used only in the FA model.

<!--Device-Sensor-static unsubscribeStepCounter(): void--><!--Device-Sensor-static unsubscribeStepCounter(): void-End-->

**System capability:** SystemCapability.Sensors.Sensor.Lite
