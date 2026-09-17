# SubscribeStepCounterOptions

Defines the type of data to return for a subscription to data changes of the step counter sensor.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** PEDOMETER

**Required permissions:** ohos.permission.ACTIVITY_MOTION

**System capability:** SystemCapability.Sensors.Sensor.Lite

## Modules to Import

```TypeScript
import { Sensor, AccelerometerResponse, BarometerResponse, CompassResponse, DeviceOrientationResponse, GetOnBodyStateOptions, GyroscopeResponse, HeartRateResponse, LightResponse, OnBodyStateResponse, ProximityResponse, StepCounterResponse, SubscribeBarometerOptions, SubscribeCompassOptions, SubscribeDeviceOrientationOptions, SubscribeGyroscopeOptions, SubscribeHeartRateOptions, SubscribeLightOptions, SubscribeOnBodyStateOptions, SubscribeProximityOptions, SubscribeStepCounterOptions, subscribeAccelerometerOptions } from '@kit.SensorServiceKit';
```

## fail

```TypeScript
fail?: (data: string, code: number) => void
```

Callback invoked when an API call fails.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [on](arkts-sensorservice-sensor-on-f.md)

**Required permissions:** ohos.permission.ACTIVITY_MOTION

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Sensors.Sensor.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | string | Yes |  |
| code | number | Yes |  |

## success

```TypeScript
success: (data: StepCounterResponse) => void
```

Defines a **StepCounterResponse** object.

**Since:** 3

**Deprecated since:** 8

**Substitutes:** [on](arkts-sensorservice-sensor-on-f.md)

**Required permissions:** ohos.permission.ACTIVITY_MOTION

**Model restriction:** This API can be used only in the FA model.

**System capability:** SystemCapability.Sensors.Sensor.Lite

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| data | [StepCounterResponse](arkts-sensorservice-system-sensor-stepcounterresponse-i.md) | Yes |  |
