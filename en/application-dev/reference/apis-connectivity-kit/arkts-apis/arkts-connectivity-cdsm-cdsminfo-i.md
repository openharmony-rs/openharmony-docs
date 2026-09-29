# CdsmInfo

```TypeScript
interface CdsmInfo
```

Represents the CDSM information.

**Since:** 26.0.0

<!--Device-cdsm-interface CdsmInfo--><!--Device-cdsm-interface CdsmInfo-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

## Modules to Import

```TypeScript
import { cdsm } from '@kit.ConnectivityKit';
```

## members

```TypeScript
members: CdsmMemberInfo[]
```

Array of member device information in the coordinated devices set. Each element in the array contains the device address and connection status.

**Type:** [CdsmMemberInfo](arkts-connectivity-cdsm-cdsmmemberinfo-i.md)[]

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-CdsmInfo-members: CdsmMemberInfo[]--><!--Device-CdsmInfo-members: CdsmMemberInfo[]-End-->

**System capability:** SystemCapability.Communication.NearLink.Base
