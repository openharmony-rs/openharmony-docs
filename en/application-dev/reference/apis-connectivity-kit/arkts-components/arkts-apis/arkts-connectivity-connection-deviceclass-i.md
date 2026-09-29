# DeviceClass

```TypeScript
interface DeviceClass
```

Describes the class of a bluetooth device.

**Since:** 10

<!--Device-connection-interface DeviceClass--><!--Device-connection-interface DeviceClass-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { connection } from '@kit.ConnectivityKit';
```

## classOfDevice

```TypeScript
classOfDevice: number
```

Class of the device.

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-DeviceClass-classOfDevice: int--><!--Device-DeviceClass-classOfDevice: int-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## majorClass

```TypeScript
majorClass: MajorClass
```

Major classes of Bluetooth devices.

**Type:** [MajorClass](arkts-connectivity-connection-majorclass-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-DeviceClass-majorClass: MajorClass--><!--Device-DeviceClass-majorClass: MajorClass-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core

## majorMinorClass

```TypeScript
majorMinorClass: MajorMinorClass
```

Major and minor classes of Bluetooth devices.

**Type:** [MajorMinorClass](arkts-connectivity-connection-majorminorclass-t.md)

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-DeviceClass-majorMinorClass: MajorMinorClass--><!--Device-DeviceClass-majorMinorClass: MajorMinorClass-End-->

**System capability:** SystemCapability.Communication.Bluetooth.Core
