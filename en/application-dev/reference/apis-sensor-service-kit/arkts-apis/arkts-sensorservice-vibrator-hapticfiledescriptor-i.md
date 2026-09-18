# HapticFileDescriptor

Describes the FD of a custom vibration configuration file. Ensure that the file is available, and the parameters in it can be obtained from the sandbox path through the [fileIo.open](../../../reference/apis-core-file-kit/js-apis-file-fs.md#fileioopen) API or from the HAP resource through the [getRawFd](../../apis-localization-kit/arkts-apis/arkts-localization-resourcemanager-resourcemanager-i.md#getrawfd) API. The application scenario is as follows: The vibration sequence is stored in a file and vibration needs to be triggered based on the offset and length. For details about the storage format of the vibration sequence, see [Vibration Effect Description](../../../device/sensor/vibrator-guidelines.md#vibration-effect-description).

**Since:** 10

**System capability:** SystemCapability.Sensors.MiscDevice

## Modules to Import

```TypeScript
import { vibrator } from '@kit.SensorServiceKit';
```

## fd

```TypeScript
fd: number
```

FD of the custom vibration configuration file.

**Type:** number

**Since:** 10

**System capability:** SystemCapability.Sensors.MiscDevice

## length

```TypeScript
length?: number
```

Resource length, in bytes. The default value is the length from the offset position to the end of the file, and the value cannot exceed the valid range of the file.

**Type:** number

**Since:** 10

**System capability:** SystemCapability.Sensors.MiscDevice

## offset

```TypeScript
offset?: number
```

Offset from the start position of the file, in bytes. The default value is the start position of the file, and the value cannot exceed the valid range of the file.

**Type:** number

**Since:** 10

**System capability:** SystemCapability.Sensors.MiscDevice
