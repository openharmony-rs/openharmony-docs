# DeviceInformation

```TypeScript
interface DeviceInformation
```

Describes the remote device information.

**Since:** 26.0.0

<!--Device-remoteDevice-interface DeviceInformation--><!--Device-remoteDevice-interface DeviceInformation-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

## Modules to Import

```TypeScript
import { remoteDevice } from '@kit.ConnectivityKit';
```

## manufacturerData

```TypeScript
manufacturerData: string
```

The manufacturer data of the remote device. The maximum length is 255.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-DeviceInformation-manufacturerData: string--><!--Device-DeviceInformation-manufacturerData: string-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

## modelData

```TypeScript
modelData: string
```

The model data of the remote device. The maximum length is 255.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-DeviceInformation-modelData: string--><!--Device-DeviceInformation-modelData: string-End-->

**System capability:** SystemCapability.Communication.NearLink.Base
