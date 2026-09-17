# SensorFrequency

```TypeScript
type SensorFrequency = 'game' | 'ui' | 'normal'
```

Defines the reporting frequency mode of the sensor.

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.Sensors.Sensor

| Type | Description |
| --- | --- |
| 'game' | Game mode, which specifies a sensor data reporting frequency of 20,000,000 ns. This parameter takes effect only when the frequency is within the frequency range supported by the hardware. |
| 'ui' | UI mode, which specifies a sensor data reporting frequency of 60,000,000 ns. This parameter takes effect only when the frequency is within the frequency range supported by the hardware. |
| 'normal' | Normal mode, which specifies a sensor data reporting frequency of 200,000,000 ns. This parameter takes effect only when the frequency is within the frequency range supported by the hardware. |
