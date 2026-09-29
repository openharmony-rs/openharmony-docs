# SensorFrequency

```TypeScript
type SensorFrequency = 'game' | 'ui' | 'normal'
```

Defines the sensor reporting frequency modes. The predefined frequency levels are provided, allowing you to quickly set the reporting frequency.

**Atomic service API**: This API can be used in atomic services since API version 11.

**Since:** 11

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-sensor-type SensorFrequency = 'game' | 'ui' | 'normal'--><!--Device-sensor-type SensorFrequency = 'game' | 'ui' | 'normal'-End-->

**System capability:** SystemCapability.Sensors.Sensor

| Type | Description |
| --- | --- |
| 'game' | Game mode, which specifies a sensor data reporting frequency of 20,000,000 ns. This mode is applicable to game apps that are sensitive to data delay. This parameter takes effect only when the frequency is within the frequency range supported by the hardware. |
| 'ui' | UI mode, which specifies a sensor data reporting frequency of 60,000,000 ns. This mode is applicable to UI interaction apps that have moderate requirements on data update. This parameter takes effect only when the frequency is within the frequency range supported by the hardware. |
| 'normal' | Normal mode, which specifies a sensor data reporting frequency of 200,000,000 ns. This mode isapplicable to common apps that do not require high data update frequency. This parameter takes effect only when the frequency is within the frequency range supported by the hardware. |
