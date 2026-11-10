# getPowerSubMode

## Modules to Import

```TypeScript
import { power } from '@kit.BasicServicesKit';
```

## getPowerSubMode

```TypeScript
function getPowerSubMode(): DevicePowerSubMode
```

Obtains the power sub-mode of this device. To query the power mode, use [getPowerMode](arkts-basicservices-power-getpowermode-f.md).

When the current power mode does not support sub-mode, SUB_MODE_INVALID is returned.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-power-function getPowerSubMode(): DevicePowerSubMode--><!--Device-power-function getPowerSubMode(): DevicePowerSubMode-End-->

**System capability:** SystemCapability.PowerManager.PowerManager.Core

**Return value:**

| Type | Description |
| --- | --- |
| [DevicePowerSubMode](arkts-basicservices-power-devicepowersubmode-e.md) | Power sub-mode. Returns SUB_MODE_INVALID when the current power mode does not support sub-mode. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [4900101](../errorcode-power.md#4900101-service-connection-failure) | Failed to connect to the service. |
