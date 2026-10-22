# @ohos.multimodalInput.infraredEmitter(IR Management)

The **infraredEmitter** module generates IR signals of the specified frequency and size, and queries the frequency range supported by the device.

**Since:** 12

<!--Device-unnamed-declare namespace infraredEmitter--><!--Device-unnamed-declare namespace infraredEmitter-End-->

**System capability:** SystemCapability.MultimodalInput.Input.InfraredEmitter

## Modules to Import

```TypeScript
import { infraredEmitter } from '@kit.InputKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getInfraredFrequencies](arkts-input-infraredemitter-getinfraredfrequencies-f.md#getinfraredfrequencies-1) | Queries the frequency range of the infrared signals supported by the device. It is recommended that you first use [hasIrEmitter](arkts-input-infraredemitter-hasiremitter-f.md) to check whether the device supports an infrared emitter. |
| [hasIrEmitter](arkts-input-infraredemitter-hasiremitter-f.md#hasiremitter-1) | Checks whether the device has an infrared emitter. This API uses a promise to return the result. |
| [transmitInfrared](arkts-input-infraredemitter-transmitinfrared-f.md#transmitinfrared-1) | Generates IR signals at the specified frequency and level. |

### Interfaces

| Name | Description |
| --- | --- |
| [InfraredFrequency](arkts-input-infraredemitter-infraredfrequency-i.md) | Defines the frequency range of IR signals. |
