# Usage

```TypeScript
type Usage = 'unknown' | 'alarm' | 'ring' | 'notification' | 'communication''touch' | 'media' | 'physicalFeedback' | 'simulateReality'
```

Enumerates the vibration scenarios.

**Atomic service API**: This API can be used in atomic services since API version 11.

<!--RP1End-->

**Since:** 9

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 11.

<!--Device-vibrator-type Usage = 'unknown' | 'alarm' | 'ring' | 'notification' | 'communication' |  'touch' | 'media' | 'physicalFeedback' | 'simulateReality'--><!--Device-vibrator-type Usage = 'unknown' | 'alarm' | 'ring' | 'notification' | 'communication' |  'touch' | 'media' | 'physicalFeedback' | 'simulateReality'-End-->

**System capability:** SystemCapability.Sensors.MiscDevice

| Type | Description |
| --- | --- |
| 'unknown' | Unknown scenario, with the lowest priority. This parameter has a fixed value of **unknown**. |
| 'alarm' | Vibration for alarms. This parameter has a fixed value of **alarm**. |
| 'ring' | Vibration for ringing. This parameter has a fixed value of **ring**. |
| 'notification' | Vibration for notification. This parameter has a fixed value of **notification**. |
| 'communication' | Vibration for communication. This parameter has a fixed value of **communication**. |
| 'touch' | Vibration for touch. This parameter has a fixed value of **touch**. |
| 'media' | Vibration for media. This parameter has a fixed value of **media**. |
| 'physicalFeedback' | Vibration for physical feedback. This parameter has a fixed value of **physicalFeedback**. |
| 'simulateReality' | Vibration for simulated reality. This parameter has a fixed value of **simulateReality**. |
