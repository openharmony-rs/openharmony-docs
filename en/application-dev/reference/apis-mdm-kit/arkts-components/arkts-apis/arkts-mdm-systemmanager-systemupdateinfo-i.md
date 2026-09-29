# SystemUpdateInfo

```TypeScript
export interface SystemUpdateInfo
```

Represents information about the system version to update.

**Since:** 12

<!--Device-systemManager-export interface SystemUpdateInfo--><!--Device-systemManager-export interface SystemUpdateInfo-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## Modules to Import

```TypeScript
import { systemManager } from '@kit.MDMKit';
```

## firstReceivedTime

```TypeScript
firstReceivedTime: number
```

Time when the system update package is received for the first time, in seconds.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-SystemUpdateInfo-firstReceivedTime: number--><!--Device-SystemUpdateInfo-firstReceivedTime: number-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## packageType

```TypeScript
packageType: string
```

Type of the system update package to update. The value can be **normal** or **patch**.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-SystemUpdateInfo-packageType: string--><!--Device-SystemUpdateInfo-packageType: string-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

## versionName

```TypeScript
versionName: string
```

System version to update.

**Type:** string

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

<!--Device-SystemUpdateInfo-versionName: string--><!--Device-SystemUpdateInfo-versionName: string-End-->

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager
