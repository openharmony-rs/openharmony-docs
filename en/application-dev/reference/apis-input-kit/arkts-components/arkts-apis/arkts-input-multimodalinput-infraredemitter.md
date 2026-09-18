# @ohos.multimodalInput.infraredEmitter(IR Management)

The **infraredEmitter** module generates IR signals of the specified frequency and size, and queries the frequency range supported by the device.

**Since:** 12

**System capability:** SystemCapability.MultimodalInput.Input.InfraredEmitter

## Modules to Import

```TypeScript
import { infraredEmitter } from '@kit.InputKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getInfraredFrequencies](arkts-input-infraredemitter-getinfraredfrequencies-f.md) | Queries the frequency range of IR signals supported by the device. |
| [hasIrEmitter](arkts-input-infraredemitter-hasiremitter-f.md) | Checks whether the device has an infrared transmitter. This API uses a promise to return the result. |
| [transmitInfrared](arkts-input-infraredemitter-transmitinfrared-f.md) | Generates IR signals at the specified frequency and level. |

### Interfaces

| Name | Description |
| --- | --- |
| [InfraredFrequency](arkts-input-infraredemitter-infraredfrequency-i.md) | Defines the frequency range of IR signals. |
