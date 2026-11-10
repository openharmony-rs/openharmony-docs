# getPowerMode

## Modules to Import

```TypeScript
import { power } from '@kit.BasicServicesKit';
```

## getPowerMode

```TypeScript
function getPowerMode(): DevicePowerMode
```

Obtains the power mode of the current device. Different power modes correspond to different device behavior policies. Developers can adjust application behavior based on the returned mode value to adapt to the current mode. For the definition and description of each mode, see DevicePowerMode. To query the sub-mode, use [getPowerSubMode](arkts-basicservices-power-getpowersubmode-f.md).

**Since:** 9

<!--Device-power-function getPowerMode(): DevicePowerMode--><!--Device-power-function getPowerMode(): DevicePowerMode-End-->

**System capability:** SystemCapability.PowerManager.PowerManager.Core

**Return value:**

| Type | Description |
| --- | --- |
| [DevicePowerMode](arkts-basicservices-power-devicepowermode-e.md) | Indicates the power mode of the current device. The value can be Standard, Power Saving, Performance, or Super Power Saving. When the power mode of the current device fails to be obtained, the value 0 is returned. The value is not within the value range defined by the [DevicePwerMode](arkts-basicservices-power-devicepowermode-e.md) enumeration. Developers should check whether the return value is a valid enumerated value (600 or more). |

**Examples**

```TypeScript
let mode = power.getPowerMode();
console.info('power mode: ' + mode);
```
