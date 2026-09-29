# SensorInfoParam

```TypeScript
interface SensorInfoParam
```

Defines sensor parameters, including **deviceId** and **sensorIndex**.

**Atomic service API**: This API can be used in atomic services since API version 19.

**Since:** 19

<!--Device-sensor-interface SensorInfoParam--><!--Device-sensor-interface SensorInfoParam-End-->

**System capability:** SystemCapability.Sensors.Sensor

## Modules to Import

```TypeScript
import { sensor } from '@kit.SensorServiceKit';
```

## deviceId

```TypeScript
deviceId?: number
```

ID of the device to which the target sensor belongs. The default value is **-1**, which indicates the local device. You can obtain the ID of a remote device through [sensor.on('sensorStatusChange')](arkts-sensorservice-sensor-on-f.md#onsensorstatuschange) or [getSensorList](arkts-sensorservice-sensor-getsensorlist-f.md).

**Type:** number

**Since:** 19

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 19.

<!--Device-SensorInfoParam-deviceId?: int--><!--Device-SensorInfoParam-deviceId?: int-End-->

**System capability:** SystemCapability.Sensors.Sensor

## sensorIndex

```TypeScript
sensorIndex?: number
```

Index of the target sensor. A sensor type may have multiple instances. The default value is **0**, which indicates the default sensor on the device. You can use [getSensorList](arkts-sensorservice-sensor-getsensorlist-f.md) or [sensor.on('sensorStatusChange')](arkts-sensorservice-sensor-on-f.md#onsensorstatuschange) to obtain the sensor index.

**Type:** number

**Since:** 19

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 19.

<!--Device-SensorInfoParam-sensorIndex?: int--><!--Device-SensorInfoParam-sensorIndex?: int-End-->

**System capability:** SystemCapability.Sensors.Sensor
