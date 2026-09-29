# Options

```TypeScript
interface Options
```

Sets the sensor reporting frequency and sensor selection parameters.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Since:** 8

<!--Device-sensor-interface Options--><!--Device-sensor-interface Options-End-->

**System capability:** SystemCapability.Sensors.Sensor

## Modules to Import

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## interval

```TypeScript
interval?: number | SensorFrequency
```

Sets the interval for reporting sensor data. Default value: 200,000,000 ns (200 ms) Unit: ns. For details about the value range, see the **minSamplePeriod** and **maxSamplePeriod** of each sensor. You can query the value range by calling [getSingleSensor](arkts-sensorservice-sensor-getsinglesensor-f.md). You are advised to set a proper reporting frequency based on service requirements. A smaller value indicates more frequent reporting. If the configured frequency is greater than the maximum value, the maximum value is used for data reporting. If the configured frequency is less than the minimum value, the minimum value is used for data reporting.

**Type:** number &#124; [SensorFrequency](arkts-sensorservice-sensor-sensorfrequency-t.md)

**Since:** 8

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-Options-interval?: long | SensorFrequency--><!--Device-Options-interval?: long | SensorFrequency-End-->

**System capability:** SystemCapability.Sensors.Sensor

## sensorInfoParam

```TypeScript
sensorInfoParam?: SensorInfoParam
```

The sensor transfers the settings parameter, which can specify **deviceId** and **sensorIndex** to select the target sensor in multi-sensor scenarios. <br>**Atomic service API**: This API can be used in atomic services since API version 19.

**Type:** [SensorInfoParam](arkts-sensorservice-sensor-sensorinfoparam-i.md)

**Since:** 19

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 19.

<!--Device-Options-sensorInfoParam?: SensorInfoParam--><!--Device-Options-sensorInfoParam?: SensorInfoParam-End-->

**System capability:** SystemCapability.Sensors.Sensor
