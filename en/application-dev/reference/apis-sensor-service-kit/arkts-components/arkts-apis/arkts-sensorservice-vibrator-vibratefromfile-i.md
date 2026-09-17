# VibrateFromFile

Represents a custom vibration pattern. It is supported only by certain devices. An error code will be returned if a device does not support this vibration mode. You can pass **VibrateFromFile** to [VibrateEffect9+](arkts-sensorservice-vibrator-vibrateeffect-t.md) to specify a custom vibration pattern when calling [vibrator.startVibration9+](arkts-sensorservice-vibrator-startvibration-f.md) or [vibrator.startVibration9+](arkts-sensorservice-vibrator-startvibration-f.md).

**Since:** 10

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

**System capability:** SystemCapability.Sensors.MiscDevice

## type

```TypeScript
type: 'file'
```

The value **file** means vibration according to a vibration configuration file.

**Type:** 'file'

**Since:** 10

**System capability:** SystemCapability.Sensors.MiscDevice
