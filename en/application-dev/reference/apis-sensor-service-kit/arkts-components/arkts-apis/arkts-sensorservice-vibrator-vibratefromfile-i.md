# VibrateFromFile

```TypeScript
interface VibrateFromFile
```

Represents a custom vibration pattern. It is supported only by certain devices. An error code will be returned if a device does not support this vibration mode. When [vibrator.startVibration&lt;sup&gt;9+&lt;/sup&gt;](arkts-sensorservice-vibrator-startvibration-f.md) or [vibrator.startVibration&lt;sup&gt;9+&lt;/sup&gt;](arkts-sensorservice-vibrator-startvibration-f.md#startvibration-1) is called, the value of [VibrateEffect&lt;sup&gt;9+&lt;/sup&gt;](arkts-sensorservice-vibrator-vibrateeffect-t.md) can be **VibrateFromFile**, indicating that a custom vibration pattern is triggered.

**Since:** 10

<!--Device-vibrator-interface VibrateFromFile--><!--Device-vibrator-interface VibrateFromFile-End-->

**System capability:** SystemCapability.Sensors.MiscDevice

## Modules to Import

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
```

## hapticFd

```TypeScript
hapticFd: HapticFileDescriptor
```

File descriptor (FD) of the vibration configuration file.

**Type:** [HapticFileDescriptor](arkts-sensorservice-vibrator-hapticfiledescriptor-i.md)

**Since:** 10

<!--Device-VibrateFromFile-hapticFd: HapticFileDescriptor--><!--Device-VibrateFromFile-hapticFd: HapticFileDescriptor-End-->

**System capability:** SystemCapability.Sensors.MiscDevice

## type

```TypeScript
type: 'file'
```

The value **file** means vibration according to a vibration configuration file.

**Type:** 'file'

**Since:** 10

<!--Device-VibrateFromFile-type: 'file'--><!--Device-VibrateFromFile-type: 'file'-End-->

**System capability:** SystemCapability.Sensors.MiscDevice
