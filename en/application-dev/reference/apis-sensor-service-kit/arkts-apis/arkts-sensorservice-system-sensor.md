# @system.sensor(Sensor module)

The **@system.sensor** module is a sensor data subscription module for lite wearables. It provides the data
 subscription and subscription cancellation capabilities for the acceleration, compass, distance, ambient light,
 pedometer, barometric pressure, heart rate, device wearing status, device orientation, and gyroscope sensors.
 This module helps apps obtain sensor data change notifications in real time to implement functions such as fitness
 monitoring, health tracking, environment sensing, direction identification, and screen adaptation. Each sensor
 provides subscription and unsubscription APIs. The wearing status sensor additionally provides the **getOnBodyState**
 API for a single query.
 For devices other than lightweight wearables, this module is no longer maintained since API version 8. You are
 advised to use the [@ohos.sensor](arkts-sensorservice-sensor.md) module instead.
 This module uses the subscription-unsubscription mode. You can call **subscribe** to subscribe to data, and the data
 will be reported through a callback when it changes. You can call **unsubscribe** to cancel the subscription.
 **subscribe** and **unsubscribe** must be used in pairs. If an app subscribes to the same sensor multiple times, only
 the last subscription takes effect. For the acceleration, device orientation, and gyroscope sensors, you can
 configure the callback frequency using **interval**. The default value is **normal** (200 ms per callback).
 All APIs require hardware support and can be debugged only on real devices. Some APIs may have device behavior
 differences. For details, see the description of each API.

> **NOTE**

> - Module maintenance policy:
 > >     - For lite wearables, this module is constantly maintained and available.
 > >     - For other device types, this module is no longer maintained since API version 8, and you are advised to use
 >  the new [@ohos.sensor](arkts-sensorservice-sensor.md) module.
 > - The initial APIs of this module are supported since API version 3. Newly added APIs will be marked with a
 > superscript to indicate their earliest API version.
 > - This module requires hardware support and can only be debugged on real devices.
 > - To reduce performance overhead, you are advised to unsubscribe from the sensor data in the **onDestroy**
 > callback.



## Modules to Import

```TypeScript
import { Sensor, AccelerometerResponse, BarometerResponse, CompassResponse, DeviceOrientationResponse, GetOnBodyStateOptions, GyroscopeResponse, HeartRateResponse, LightResponse, OnBodyStateResponse, ProximityResponse, StepCounterResponse, SubscribeBarometerOptions, SubscribeCompassOptions, SubscribeDeviceOrientationOptions, SubscribeGyroscopeOptions, SubscribeHeartRateOptions, SubscribeLightOptions, SubscribeOnBodyStateOptions, SubscribeProximityOptions, SubscribeStepCounterOptions, subscribeAccelerometerOptions } from '@kit.SensorServiceKit';
```

## Summary

### Classes

| Name | Description |
| --- | --- |
| [Sensor](arkts-sensorservice-system-sensor-sensor-c.md) |  |

### Interfaces

| Name | Description |
| --- | --- |
| [AccelerometerResponse](arkts-sensorservice-system-sensor-accelerometerresponse-i.md) | Callback invoked when the acceleration sensor data changes. The callback returns the acceleration data of the device on the x, y, and z axes. |
| [BarometerResponse](arkts-sensorservice-system-sensor-barometerresponse-i.md) | Defines a response object of the callback function after the barometric pressure sensor data is changed, including the atmospheric pressure value. |
| [CompassResponse](arkts-sensorservice-system-sensor-compassresponse-i.md) | Callback function response object after the compass data changes, including the degree of the direction that the device faces. |
| [DeviceOrientationResponse](arkts-sensorservice-system-sensor-deviceorientationresponse-i.md) | Defines a response object of the callback function after the device orientation sensor data changes, including the three rotation angles of the device. |
| [GetOnBodyStateOptions](arkts-sensorservice-system-sensor-getonbodystateoptions-i.md) | Sets the parameters for subscribing to the device wearing status, including the callback function. The wearing status can be worn or not worn. |
| [GyroscopeResponse](arkts-sensorservice-system-sensor-gyroscoperesponse-i.md) | Defines a response object of the callback function after the gyroscope sensor data changes, including the rotational velocity data of the device on the x, y, and z axes. |
| [HeartRateResponse](arkts-sensorservice-system-sensor-heartrateresponse-i.md) | Defines a response object of the callback function after the heart rate sensor data is changed, including the heart rate value. |
| [LightResponse](arkts-sensorservice-system-sensor-lightresponse-i.md) | Callback invoked when the ambient light sensor data changes. The response object contains the ambient light intensity data. |
| [OnBodyStateResponse](arkts-sensorservice-system-sensor-onbodystateresponse-i.md) | Defines a response object of the device wearing status, including the data indicating whether the device is worn. |
| [ProximityResponse](arkts-sensorservice-system-sensor-proximityresponse-i.md) | Callback function response object after the proximity sensor data changes, including the distance between a visible object and the device screen. |
| [StepCounterResponse](arkts-sensorservice-system-sensor-stepcounterresponse-i.md) | Defines a response object of the callback function invoked when the step counter sensor data changes, including the accumulated step count recorded after the step counter sensor is restarted. |
| [subscribeAccelerometerOptions](arkts-sensorservice-system-sensor-subscribeaccelerometeroptions-i.md) | Sets the parameters for subscribing to the acceleration sensor, including the callback frequency and callback function. |
| [SubscribeBarometerOptions](arkts-sensorservice-system-sensor-subscribebarometeroptions-i.md) | Configures the parameters for subscribing to the barometric pressure sensor, including the callback function. |
| [SubscribeCompassOptions](arkts-sensorservice-system-sensor-subscribecompassoptions-i.md) | Sets the parameters for subscribing to the compass sensor, including the callback function. |
| [SubscribeDeviceOrientationOptions](arkts-sensorservice-system-sensor-subscribedeviceorientationoptions-i.md) | Sets the parameters for subscribing to the device orientation sensor, including the callback frequency and callback function. |
| [SubscribeGyroscopeOptions](arkts-sensorservice-system-sensor-subscribegyroscopeoptions-i.md) | Defines the parameters for subscribing to the gyroscope sensor, including the callback frequency and callback function. |
| [SubscribeHeartRateOptions](arkts-sensorservice-system-sensor-subscribeheartrateoptions-i.md) | Configures the parameters for subscribing to the heart rate sensor, including the callback function. The callback frequency of heart rate data is fixed at 5 seconds per time and cannot be configured using the interval parameter. |
| [SubscribeLightOptions](arkts-sensorservice-system-sensor-subscribelightoptions-i.md) | Sets the parameters for subscribing to the ambient light sensor, including the callback function. |
| [SubscribeOnBodyStateOptions](arkts-sensorservice-system-sensor-subscribeonbodystateoptions-i.md) | Sets the parameters for subscribing to the device wearing status, including the callback function. The wearing status can be worn or not worn. |
| [SubscribeProximityOptions](arkts-sensorservice-system-sensor-subscribeproximityoptions-i.md) | Sets the parameters for subscribing to the distance sensor, including the callback function. |
| [SubscribeStepCounterOptions](arkts-sensorservice-system-sensor-subscribestepcounteroptions-i.md) | Sets the parameters for subscribing to the step counter sensor, including the callback function. |
